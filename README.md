## House Price Prediction in Ames, Iowa
A predictive model for house prices in Ames, Iowa, using Python, scikit-learn, and statsmodels. Navigate to the report document in the report folder for details.
Overview
This project develops a predictive model for house prices in Ames, Iowa, to assist a real estate company in purchasing, renovating, and reselling properties. The model employs exploratory data analysis (EDA), preprocessing, and regression techniques (multiple linear regression, quadratic regression, and LASSO regression) to achieve an Adjusted R-squared of 80.0% on the test set. Navigate to the report document in `report` folder for details.

## Dataset

Source: Kaggle: Ames Housing Dataset (Also available in data folder as Ames.csv)
Features: 80 predictors, including OverallQual, GrLivArea, TotalBsmtSF, Neighborhood, KitchenQual, and engineered features (TotalSF, Age, Qual_GrLivArea)
Size: 1460 rows, split into 1022 training and 438 testing observations

## Methodology

EDA: Identified skewness in SalePrice (mean $180,921, median $163,000), strong correlations (OverallQual: 0.79, GrLivArea: 0.71), and missing values (e.g., LotFrontage: 17.74%).
Preprocessing: Imputed missing values (medians for numerical, "None" for categorical), log-transformed SalePrice and key predictors, encoded categorical variables (dummy and ordinal), and created features (TotalSF, Age, Qual_GrLivArea).
Modeling: Applied multiple linear regression, quadratic regression (with squared terms for Log_GrLivArea, Log_TotalBsmtSF), and LASSO regression with cross-validated alpha.
Validation: Evaluated on test set with MSE, RMSE, Adjusted R-squared, and 5-fold cross-validation RMSE. Residual diagnostics (Breusch-Pagan, Shapiro-Wilk) and VIF were used to check assumptions.

## Results

Adjusted R-squared: 0.8000 (test set)
Test RMSE: 0.1286 (log scale, ~12.86% error on original price scale)
Significant Predictors: Log_GrLivArea (18.70% price increase per standard deviation), Neighborhood_StoneBr (11.37%), Exterior1st_BrkFace (10.17%), Neighborhood_NoRidge (9.35%), Qual_GrLivArea (8.78%)
LASSO Selected Features: 98 predictors, including OverallQual, Log_GrLivArea, TotalSF, and Neighborhood dummies

## Limitations

Multicollinearity: High VIF for OverallQual (441.80) and Qual_GrLivArea (565.00), indicating potential redundancy in predictors.
Residual Diagnostics: Breusch-Pagan and Shapiro-Wilk p-values (0.0000) reject homoskedasticity and normality, suggesting unmodeled patterns or omitted variables (e.g., school quality).
Feature Set Size: Large number of features (227) may cause computational challenges; further feature selection could improve efficiency.

## License
All rights reserved
