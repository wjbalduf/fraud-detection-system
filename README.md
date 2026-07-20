# Fraud Detection System using Machine Learning

## Overview

Financial fraud costs organizations billions of dollars each year, making accurate fraud detection critical for minimizing financial losses and protecting customers.

This project develops and evaluates multiple machine learning models to detect fraudulent financial transactions using the PaySim synthetic banking dataset. The project follows an end-to-end data science workflow, including data cleaning, exploratory data analysis, feature engineering, model development, model evaluation, and business-focused recommendations.

---

## Business Problem

Traditional rule-based fraud detection systems often struggle to identify new fraud patterns while minimizing false positives.

The objective of this project is to build a machine learning model capable of accurately identifying fraudulent transactions while reducing unnecessary fraud alerts.

---

## Dataset

This project uses the "PaySim" synthetic financial transaction dataset from Kaggle.

The dataset contains over **6.3 million** simulated mobile money transactions and includes transaction amounts, account balances, transaction types, and fraud labels.

The dataset is not included in this repository because it exceeds GitHub's file size limits.

Download it here:

https://www.kaggle.com/datasets/ealaxi/paysim1

After downloading, place the dataset here:

```
data/paysim.csv
```

---

## Project Workflow

- Data Cleaning
- Exploratory Data Analysis (EDA)
- Feature Engineering
- Machine Learning Modeling
- Model Evaluation
- Business Insights & Recommendations

---

## Technologies Used

### Programming

- Python

### Libraries

- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- XGBoost
- Joblib

### Machine Learning Models

- Logistic Regression
- Random Forest
- XGBoost

---

## Feature Engineering

Several behavioral features were created to improve fraud detection performance, including:

- Sender balance change
- Destination balance change
- Sender balance removed percentage
- Balance consistency features
- High-value transaction indicator
- One-hot encoded transaction types

---

## Model Performance

| Model | Precision | Recall | F1 Score | ROC-AUC | Average Precision |
|-------|-----------|--------|----------|---------|-------------------|
| Logistic Regression | 0.024 | 0.963 | 0.047 | 0.991 | 0.560 |
| Random Forest | 1.000 | 0.998 | 0.999 | 0.999 | 0.998 |
| XGBoost | 0.176 | 0.995 | 0.299 | 0.995 | 0.178 |

Random Forest achieved the strongest overall performance and was selected as the preferred model for this dataset.

---

## Key Business Insights

- Fraud represented only **0.13%** of all transactions, creating a highly imbalanced classification problem.
- Fraud occurred almost exclusively during **TRANSFER** and **CASH_OUT** transactions.
- Fraudulent transactions generally involved significantly larger transaction amounts.
- Abnormal sender account balance behavior was the strongest indicator of fraud.
- Random Forest correctly detected **1,639 of 1,643** fraudulent transactions while producing **zero false positives** on the PaySim test dataset.

---

## Project Structure

```
fraud-detection-system/
│
├── data/
│   ├── paysim.csv                  (download separately)
│   └── paysim_engineered.csv       (generated automatically)
│
├── images/
│
├── notebooks/
│   ├── 01_EDA.ipynb
│   ├── 02_Feature_Engineering.ipynb
│   ├── 03_Modeling.ipynb
│   ├── 04_Model_Evaluation.ipynb
│   └── 05_Business_Insights.ipynb
│
├── results/
│   ├── logistic_model.pkl
│   ├── random_forest_model.pkl
│   ├── xgboost_model.pkl
│   ├── scaler.pkl
│   ├── train_test_split.pkl
│   ├── model_metrics.csv
│   ├── rf_feature_importance.csv
│   └── xgb_feature_importance.csv
│
└── README.md
```

---

## Running the Project

Run the notebooks in the following order:

1. `01_EDA.ipynb`
2. `02_Feature_Engineering.ipynb`
3. `03_Modeling.ipynb`
4. `04_Model_Evaluation.ipynb`
5. `05_Business_Insights.ipynb`

The notebooks automatically generate:

### Data

```
data/paysim_engineered.csv
```

### Trained Models

```
results/logistic_model.pkl
results/random_forest_model.pkl
results/xgboost_model.pkl
results/scaler.pkl
results/train_test_split.pkl
```

### Evaluation Results

```
results/model_metrics.csv
results/rf_feature_importance.csv
results/xgb_feature_importance.csv
```

### Visualizations

All charts are automatically saved to the `images/` folder, including:

- Fraud Distribution
- Transaction Type Distribution
- Box Plots
- Correlation Heatmap
- ROC Curve
- Precision-Recall Curve
- Confusion Matrices
- Feature Importance Charts

---

## Limitations

This project uses the PaySim synthetic dataset, which closely simulates financial transactions but does not fully capture the complexity of real-world fraud.

Some features, such as post-transaction account balances (`newbalanceOrig` and `newbalanceDest`), are available in the dataset but may not always be available in real-time production systems before transaction approval.

Future work could evaluate models using only pre-transaction information and incorporate explainable AI techniques such as SHAP values.

---

## Future Improvements

- Hyperparameter tuning using GridSearchCV or RandomizedSearchCV
- Threshold optimization for precision-recall tradeoffs
- Evaluate LightGBM and CatBoost
- Deploy as a real-time fraud detection API
- Build an interactive Power BI or Tableau dashboard for fraud monitoring

---

## Author

**William Balduf**

Bachelor of Science in Data Science  
Worcester Polytechnic Institute (WPI)
