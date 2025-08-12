# Fraud Detection Prediction Model

This project demonstrates how to **load trained machine learning models** and **predict fraud detection outcomes** for new transactions using saved preprocessing objects (`LabelEncoder`, `StandardScaler`) and multiple classifiers.  
It supports **majority voting ensemble** for improved accuracy.

## 📌 Features
- Load pre-trained models (`HistGradientBoosting`, `RandomForest`, `LogisticRegression`)
- Apply saved `LabelEncoder` for categorical features
- Apply saved `StandardScaler` with correct feature ordering
- Automatically fill missing features with default values
- Handle unseen transaction types gracefully
- Predict with each model individually
- Combine predictions via **majority voting ensemble**

## 🛠 Requirements
Install dependencies using pip:

```bash
pip install pandas numpy scikit-learn joblib
```


---

## 📌 Features
- Load pre-trained models:
  - `HistGradientBoosting`
  - `RandomForest`
  - `LogisticRegression`
- Apply saved preprocessing:
  - `LabelEncoder` for categorical features
  - `StandardScaler` for numerical features
- Auto-handle unseen categories in `transaction_type`
- Fill missing columns with safe default values
- Predict with each model individually
- **Majority voting ensemble** for final decision

---

## 📂 Repository Structure
```

Fraud-Detection/
│
├── LICENSE
├── README.md                  # Project documentation
├── requirements.txt           # Required dependencies
├── predict.py                  # Main prediction script
├── HistGradientBoosting\_model.joblib
├── Random\_Forest\_model.joblib
├── Logistic\_Regression\_model.joblib
├── label\_encoder.joblib
├── standard\_scaler.joblib
├── data/                       # (Optional) dataset storage
├── check.ipynb
├── models.ipynb
└── Fraud Detection.ipynb       # Training & analysis notebook

````

---

## 🛠 Installation

### 1️⃣ Clone the repository
```bash
git clone https://github.com/your-username/Fraud-Detection.git
cd Fraud-Detection
````

### 2️⃣ Install dependencies

```bash
pip install -r requirements.txt
```

---

## 🚀 Usage

Run predictions on sample transactions:

```bash
python predict.py
```

---

## 📊 Example Output

```
Expected numerical features for scaler: ['step' 'type' 'amount' 'oldbalanceOrg' 'newbalanceOrig' 'oldbalanceDest' 'newbalanceDest' 'isFlaggedFraud']
Known transaction types: ['CASH_IN' 'CASH_OUT' 'DEBIT' 'PAYMENT' 'TRANSFER']
Using default category 'CASH_IN' for unseen values

HistGradientBoosting Predictions:
Transaction 1: Non-Fraud (Fraud Probability: 0.0134)
Transaction 2: Fraud (Fraud Probability: 0.9231)
Transaction 3: Non-Fraud (Fraud Probability: 0.0321)

Random_Forest Predictions:
Transaction 1: Non-Fraud (Fraud Probability: 0.0100)
Transaction 2: Fraud (Fraud Probability: 0.9100)
Transaction 3: Non-Fraud (Fraud Probability: 0.0500)

Logistic_Regression Predictions:
Transaction 1: Non-Fraud (Fraud Probability: 0.0150)
Transaction 2: Fraud (Fraud Probability: 0.9000)
Transaction 3: Non-Fraud (Fraud Probability: 0.0400)

Ensemble Predictions (Majority Voting):
Transaction 1: Non-Fraud
Transaction 2: Fraud
Transaction 3: Non-Fraud
```

---

## 🧠 How It Works

1. **Load models & preprocessors**

   * `LabelEncoder` encodes the `transaction_type` column
   * `StandardScaler` standardizes numerical features

2. **Prepare new data**

   * Replace unseen transaction types with a default known category
   * Add any missing columns required by the scaler
   * Reorder columns to match training order

3. **Make predictions**

   * Each model predicts separately
   * Ensemble majority voting decides the final label

---

## 📜 License

This project is licensed under the **MIT License** — you are free to use, modify, and distribute it.

---

💡 **Tip:** Keep `.joblib` files from the same training setup to avoid feature mismatches when predicting.

