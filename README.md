# Loan Predictor
Predict if customer will sign a term loan

## Pre Processing
- No Nulls in Data
- Some columns had "." in them which causes some functions to fail, so those were changed to "_"
- Multicollinearity was found, but it was not fixed because our focus is on prediction

## EDA & Feature Engineering
- **Target:** The target variable was found to be un-balanced, so Accuracy could not be used as the validation metric
  - AUC was chosen as the validation metric
- **Numerical:** No variables were found to have normal distribution so we were transformed or bucketed
  - Variables which were found to be distributed into two groups were grouped accordingly
    - These bucketing groups were verified to have good differentiation in the target variable
  - Other variables were transformed using standard scaler
- **Categorical:** To reduce cardinality some categories were grouped that had similar scores of the target variable
  - marital - Grouped into at least once married oro not
  - education - Grouped into college versus not
  - month - Grouped into summer versus not

### K Means
Data was then prepared using one-hot encoding and vector assembler to be fed to k means clustering model
Data was assigned to 4 clusters

## Supervised Modeling
With the addition of the k means cluster label, the data was again run through vector assembler to prepare for supervised modeling.
It was split into train and test 70/30
5 Models were used:
- Logistic Regression
- Random Forest
- Gradient Boosted Trees
- Support Vector Machines
- Decision Tree
Hyperparameter grids were provided for each of these except for logistic regression
3-fold cross validation was used

### Model Evaluation
Because the data set was unabalanced AUC was chosen as the validation metric instead of Accuracy
Random Forest is the champion because it had by far the highest AUC at around 90% after being tested with different random seeds


### Prescriptive Recommendations

Based on this analysis, we have seen a higher loan rate among

*   Highly educated
*   At least once married people
*   In warmer months
  
To capitalize on that, we should focus advertising on that demographic with targeted advertising in spring or early summer
