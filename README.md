# Trust-Aware-XAI-Disease-Prediction

## Project Overview

This repository contains the computational implementation supporting a Master's dissertation investigating trust-aware Explainable Artificial Intelligence (XAI) for multiclass symptom-based disease prediction.

The research evaluates predictive machine-learning models alongside SHAP and LIME explanations, with particular emphasis on explanation agreement, stability, and robustness. Two experimental components are developed within the study:

- **Hybrid Explanation Fusion (HEF)** – combines normalised SHAP and LIME feature-attribution evidence into a unified explanation representation.
- **Trust Consistency Index (TCI)** – integrates cross-explainer agreement, LIME stability, and SHAP sensitivity robustness into a computational measure of explanation consistency.

The term "trust" in TCI refers to computational properties of explanation consistency. It should not be interpreted as directly measured human, patient, or clinician trust.

## Research Aim

To develop and evaluate a trust-aware explainable AI framework for multiclass symptom-based disease prediction by systematically examining predictive performance and the agreement, stability, and robustness of model explanations.

## Dataset

The research uses the **SympScan – Symptoms to Disease** dataset available through Kaggle.

The original dataset contains:

- 96,088 observations
- 230 binary symptom features
- 100 disease classes

Following the preprocessing and experimental data-quality validation procedures documented in the notebook, the final analytical dataset contains:

- 94,204 observations
- 230 symptom predictors
- 100 disease classes
- 0 missing values
- 0 duplicate observations

The dataset itself is not redistributed through this repository. Please obtain it from the original Kaggle source.

## Predictive Models

Five machine-learning approaches are evaluated:

- Logistic Regression
- Decision Tree
- Random Forest
- XGBoost
- Artificial Neural Network (ANN)

Model performance is evaluated primarily using accuracy and F1-score, with cross-validation and hyperparameter optimisation applied where appropriate.

## Explainable AI Framework

### SHAP

SHapley Additive exPlanations (SHAP) is used to generate feature-level attribution information describing the contribution of symptoms to model predictions.

### LIME

Local Interpretable Model-Agnostic Explanations (LIME) is used as a complementary local explanation method.

SHAP and LIME explanations are compared using:

- Top-k feature overlap
- Spearman rank correlation
- Directional agreement
- Global feature-ranking comparison

The systematic local XAI evaluation covers 100 cases representing the 100 disease classes.

## Hybrid Explanation Fusion (HEF)

HEF integrates L1-normalised SHAP and LIME feature contributions into a unified representation.

The primary implementation uses equal SHAP-LIME weighting. Weight sensitivity is additionally examined using:

- 0.1 : 0.9
- 0.3 : 0.7
- 0.5 : 0.5
- 0.7 : 0.3
- 0.9 : 0.1

HEF is evaluated using feature overlap, directional agreement, Top-1 agreement, and sensitivity to alternative weighting configurations.

## Trust Consistency Index (TCI)

TCI combines three complementary dimensions of explanation consistency:

1. **Agreement** – compatibility between SHAP and LIME explanations.
2. **Stability** – consistency of LIME explanations across repeated executions.
3. **Sensitivity Robustness** – behaviour of SHAP explanations under controlled binary symptom perturbation.

The primary TCI implementation uses equal weighting of the three components.

Additional evaluation includes:

- repeated LIME analysis
- controlled binary feature flipping
- prediction-preservation analysis
- component ablation
- Mann-Whitney U testing
- Spearman correlation with prediction confidence

## Repository Structure

```text
trust-aware-xai-disease-prediction/
│
├── README.md
├── requirements.txt
├── .gitignore
│
├── notebooks/
│   └── final_dissertation_analysis.ipynb
│
├── data/
│   └── README.md
│
└── outputs/
    ├── figures/
    └── tables/
