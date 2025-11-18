

# **Stock Price Prediction Using Deep Learning & Baseline Models**

This project explores the effectiveness of deep learning models—specifically LSTM architectures—compared to traditional baselines for **next-day stock price prediction** using daily OHLCV data from AAPL, AMZN, and QCOM (2010–2025).

It evaluates whether increased model complexity leads to better predictive performance in a domain known for **high noise and low signal**, and whether multi-stock pooled models or stock-ID-aware models provide practical improvements.

---

## **Project Overview**

The project investigates:

* Baseline models

  * Naïve persistence
  * Linear regression
* Deep learning models

  * LSTM (multi-stock pooled)
  * LSTM with stock-ID embeddings
* Optional ensemble comparison

  * HistGradientBoosting

All models are evaluated on:

* RMSE
* MAE
* MAPE
* Directional Accuracy (predicting up/down trends)

---

## **Key Findings**

* **Linear regression outperformed all LSTM models** in predicting price direction (≈52% DA).
* LSTM variants plateaued early (2–3 epochs), showing minimal ability to capture deeper structures.
* Naïve persistence achieved the lowest RMSE due to autocorrelation, but failed to predict direction.
* Deep learning did **not** provide a performance advantage when using only daily OHLCV data.
* Findings support financial literature:

  > “More model complexity doesn’t help when data has weak predictive signal.”

For full analysis, visualisations, and literature review, see the report 

---

## **Repository Structure**

```
stock-price-prediction-deep-learning/
│
├──DL.ipynb                 # full code, training, evaluation, plots
│
├── stock-price-prediction-report.docx # full research report 
│
└── README.md
```

---

## **Dataset**

* Daily OHLCV prices for AAPL, AMZN, QCOM
* Source: Yahoo Finance (2010–2025)
* Technical indicators used:

  * SMA, EMA
  * RSI
  * MACD
  * Volatility

Window size: **30–60 days**
Prediction horizon: **next-day close**

---

## **Methods**

### **1. Data Preprocessing**

* Cleaning, sorting, date parsing
* Technical indicators
* Train/val/test split (70/10/20, time-series safe)
* Standardization using `StandardScaler`
* Sliding window (W=30 or 60)

### **2. Models**

* **Naive persistence**
* **Linear Regression**
* **LSTM (pooled)**
* **LSTM + stock ID embedding**
* **HistGradientBoosting (optional baseline)**

### **3. Evaluation**

* RMSE
* MAE
* MAPE
* Directional Accuracy

---

## **Results Summary**

| Model             | RMSE        | Directional Accuracy |
| ----------------- | ----------- | -------------------- |
| Naive             | lowest RMSE | ~0–22%               |
| Linear Regression | moderate    | **≈52% (best)**      |
| LSTM (pooled)     | ~3.8–4.1    | ~47–50%              |
| LSTM + ID         | ~3.8–4.1    | ~47–49%              |
| HGB               | competitive | slightly above LSTM  |

Full charts in the report and notebook.

---

## **Conclusion**

Traditional models performed as well as, or better than, deep learning for daily stock forecasting due to the weak predictive signal in OHLCV data.
Future improvements require:

* richer features (sentiment, intraday data, macro indicators)
* alternative architectures (TCN, Transformer)
* multi-task learning
* risk-aware evaluation

---

## **Full Report**

A detailed research report covering:

* Literature review
* Methodology
* Deep learning analysis
* Comparisons
* Limitations
* Future work


