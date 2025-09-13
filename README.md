## Project Overview

This project focuses on building a machine learning model to predict house prices in the London housing market. The goal is to demonstrate a complete machine learning workflow, from initial data cleaning and feature engineering to model training, evaluation, and hyperparameter tuning. The project leverages a dataset of historical London house sales to train and compare several advanced tree-based regression models, including **Random Forest**, **LightGBM**, and **XGBoost**.

---

## Repository Contents

* `housingdata.ipynb`: This Jupyter Notebook contains the complete data cleaning and preprocessing pipeline. It transforms the raw, messy dataset into a structured format ready for machine learning.
* `random_forest_ML.ipynb`: This notebook is where the core machine learning work is performed. It includes code for data splitting, model training, evaluation, and hyperparameter tuning.
* `final_housing_data.xlsx`: This Excel file is the output of `housingdata.ipynb`. It contains the cleaned and preprocessed dataset used for training the models.
* `README.md`: This file, providing an overview of the project.

---

## Methodology

### 1. Data Cleaning and Preprocessing (`housingdata.ipynb`)

The initial dataset was a raw collection of London house sales with various inconsistencies. The following steps were performed to prepare the data:

* **Handling Missing Values**: Missing numerical values in columns like `bathrooms` and `bedrooms` were filled with the median. Rows with missing `floorAreaSqM` were dropped.
* **Feature Engineering**: New, more informative features were created, including `days_since_sold` and `outcode_encoded`, which provides a numerical representation of the average price for a given postcode area.
* **Categorical Encoding**: Text-based categorical features (`tenure`, `propertyType`, `currentEnergyRating`) were transformed into numerical data using one-hot encoding, a necessity for machine learning models.
* **Duplicate Handling**: Properties that were sold multiple times were addressed by keeping only the most recent sale record to ensure the model learns from the most relevant market data.

### 2. Model Training and Evaluation (`random_forest_ML.ipynb`)

With the data prepared, the focus shifted to building and evaluating predictive models.

* **Data Splitting**: The dataset was split into an **80% training set** and a **20% testing set** to train and validate the models' performance on unseen data.
* **Model Selection**: Three powerful tree-based regression models were chosen for a comparative analysis:
    * **Random Forest Regressor**: An ensemble model that uses bagging to build multiple independent decision trees.
    * **LightGBM & XGBoost**: Gradient boosting models that build trees sequentially to correct the errors of previous trees, often achieving state-of-the-art performance.
* **Hyperparameter Tuning**: `RandomizedSearchCV` was used to optimize the Random Forest Regressor's performance. This technique efficiently searches for the best combination of model settings (hyperparameters) to minimize prediction error.
* **Evaluation Metrics**: Model performance was measured using standard regression metrics:
    * **Mean Absolute Error (MAE)**: The average absolute difference between predicted and actual prices.
    * **Root Mean Squared Error (RMSE)**: A metric that penalizes larger errors more heavily.
    * **R² Score**: The proportion of the variance in house prices that the model can explain.

---
