# 🩺 Kaggle Playground Series - Diabetes Prediction Challenge

## 💡 Project Overview
This project focuses on building a highly accurate binary classification model to predict the probability of a patient having **diagnosed diabetes**. The dataset is sourced from the Kaggle Playground Series - Season 5, Episode 12.

The goal was to demonstrate a robust data science workflow, from exploratory data analysis (EDA) and feature engineering to advanced model tuning.

---

## 📊 Methodology and Workflow

### 1. Exploratory Data Analysis (EDA) & Cleaning
* **Target Analysis:** Identified significant **class imbalance** (Ratio of 1: [87k] vs 0: [52k]), necessitating the use of **ROC-AUC** as the primary evaluation metric.
* **Data Quality:** Confirmed **no missing values** across all 26 features.
* **Initial Insights:** Found strong positive correlation between Age, BMI, and various cardiovascular health indicators (BP, Cholesterol) and the target.

### 2. Feature Engineering & Preprocessing (Phase 2)
* **Categorical Encoding:** Applied **Ordinal Encoding** to ranked features (`income_level`, `education_level`) and **One-Hot Encoding** to nominal features (`gender`, `ethnicity`, etc.).
* **Feature Creation:** Engineered a clinically relevant feature, **Pulse Pressure**, calculated as `Systolic BP - Diastolic BP`.
* **Scaling:** Applied **Standard Scaling** to all continuous numerical features to prevent features with larger magnitudes from dominating the model.

### 3. Model Building & Tuning (Phase 3 & 4)
| Model | Purpose | Validation ROC-AUC |
| :--- | :--- | :--- |
| **Logistic Regression** | Baseline | **[0.5990 Score]** |
| **Random Forest** | Bagging Ensemble | **[0.6052 Score]** |
| **XGBoost Classifier** | Gradient Boosting | **[0.7223 Score]** |
| **Tuned XGBoost** | Hyperparameter Tuning | **[0.7251 Score]** |

* **Tuning Technique:** Used **Grid Search Cross-Validation (GridSearchCV)** with a 3-fold split to systematically find the optimal hyperparameters for XGBoost.
* **Optimal Hyperparameters:** `learning_rate`: **[0.2]**, `max_depth`: **[3]**, `n_estimators`: **[500]**

---

## 🥇 Results and Conclusions

The final, tuned **XGBoost Classifier** was trained on the full dataset and submitted to the competition.

* **Final Kaggle Test Set Score:** **[Your 0.69595]** ROC-AUC
* **Validation Accuracy:** **[Your 0.6832]**
* **Key Challenge:** The classification report revealed low **Recall (0.42)** for the 'No Diabetes' class, indicating a persistent challenge with class imbalance.

### Future Work:
* Apply **SMOTE** or **Class Weighting** to improve the model's performance on the minority class and potentially raise the overall ROC-AUC.
* Further feature selection based on the correlation matrix and feature importance scores.

---

## 🛠️ Setup Instructions
To run this project locally, clone the repository and install the dependencies:

```bash
git clone [REPO_LINK]
cd diabetes-prediction-kaggle
```
