# Brief overview of the project:



This project aimed to detect fraudulent credit card transactions using anonymised, PCA-transformed data. 

The main challenges were extreme class imbalance (only 0.17% fraud cases) and lack of interpretability due to PCA.

## Methodology

1. split the data into training, validation and test sets.
2. Standardized numerical features by fitting the scaler on the training data and applying the same transformation to the validation and test sets. 
3. Evaluated Logistic Regression, SVC, KNN, Random Forest, and XGBoost under 4 class-imbalance strategies: no resampling, random oversampling, random undersampling and SMOTE.
4. Based on F1-score and Average Precision on the validation set, selected 3 competing models: Random Forest without resampling, XGBoost with random oversampling and XGBoost with SMOTE. 
5. Performed stratified 3-fold cross-validation with grid search on the training data to hpertune both candidates. For the resampled models,resampling was performed independently within each CV training fold to prevent data leakage. (The second one got the best CV results)
6. Evaluated the hypertuned candidates on the validation set using Precision–Recall curves and Average Precision, then optimised the classification threshold for F1 score, using the PR curve.
7. Evaluated all 3 selected models, with their fixed hyperparameters and threshold, once on the untouched test set using precision, recall, F1-score, Average Precision, and the confusion matrix. 


## Results: 

The 3 models had virtually identical CV and validation AP, so neither had a meaningful advantage in overall PR performance. After selecting the operating thresholds based solely on the validation set, Random Forest achieved the higher F1 on the untouched test set, while also achieving substantially higher precision, with a much simpler pipeline. Therefore, we selected Random Forest as the final model.








