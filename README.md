# ChurnGuard — Telecom Customer Churn Prediction

An end-to-end data science project that identifies at-risk telecom customers 
and turns model predictions into an interactive Power BI dashboard with 
actionable retention strategies.

## Problem
Telecom companies lose significant revenue to customer churn. This project 
predicts which customers are likely to churn and identifies the key drivers 
behind that decision, so retention teams can act before customers leave.

## Approach
1. **EDA**: Explored churn patterns across service usage, customer service 
   calls, and geography — identified a "4th call spike" pattern (churn stays 
   low through the first 3 service calls, then spikes sharply) and an 
   International Plan churn paradox (42% churn vs. 11.5% for customers 
   without the plan).
2. **Modeling**: Compared Logistic Regression, Random Forest, and XGBoost. 
   Used class-weighting (`scale_pos_weight` / `class_weight='balanced'`) 
   instead of SMOTE to avoid data leakage between train and test sets.
3. **Model Selection**: XGBoost was selected as the final model, achieving 
   the highest F1-score (0.793) and ROC-AUC (0.902) among the three 
   candidates tested — confirming that churn drivers in this dataset are 
   non-linear.
4. **Feature Importance**: International Plan, Customer Service Calls, and 
   Voice Mail Plan emerged as the top three churn drivers.
5. **Dashboard**: Built a 3-page Power BI dashboard (Overview, Geographic, 
   Strategic Recommendations) translating model output into business action.

## Results

| Model | Precision | Recall | F1 | ROC-AUC |
|---|---|---|---|---|
| Logistic Regression | 0.343 | 0.732 | 0.467 | 0.816 |
| Random Forest | 0.758 | 0.742 | 0.750 | 0.895 |
| **XGBoost (final)** | **0.839** | **0.753** | **0.793** | **0.902** |

## Key Insights
- **International Plan** is the strongest churn driver (feature importance: 0.29)
- **Customer service calls** — churn spikes sharply after the 3rd call, 
  suggesting a proactive outreach opportunity at that threshold
- **Voice mail plan absence** correlates with higher churn — a low-cost 
  retention lever not surfaced until the feature importance analysis

## Repository Structure
