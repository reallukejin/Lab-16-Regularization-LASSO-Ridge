# Lab-16-Regularization-LASSO-Ridge
# Regularization: Buying Bias to Sell Variance

## Objective
I tested how LASSO and Ridge regularization compare to OLS when there are more predictors than training rows and only a few of them actually matter.

## Methodology
- Built a simulated dataset with 200 predictors, only 5 of them real, and 105 training rows
- Fitted OLS, LASSO and Ridge, with LASSO and Ridge each choosing their penalty by 5-fold cross-validation inside a pipeline with a scaler
- Traced the LASSO path to see the order in which variables enter as the penalty falls
- Chose the LASSO penalty by 5-fold cross-validation with the scaler refit inside every fold
- Checked LASSO's selected variables against the known truth
- Gave LASSO and Ridge two near-duplicate predictors that both matter, and compared how each handled them
- Wrote my own prompt asking an AI for a cross-validation loop, and checked its output against my own results

## Key Findings
- Test MSE was 12.9587 for OLS, 10.1128 for Ridge and 1.4219 for LASSO. OLS overfit badly, Ridge helped a little, and LASSO did by far the best because only 5 predictors were real.
- On the LASSO path, all five true predictors were in from step 6, and the first noise variable didn't enter until step 17.
- Cross-validation chose lambda = 0.1995, with a CV MSE of 1.5502.
- LASSO found 5 of 5 true predictors, with 11 false positives.
- With two near-duplicate predictors, LASSO put 4.462 on one and zero on the other, while Ridge split the weight 1.618 and 1.609.
- I went 2 rounds with the AI. Its function matched my lambda and CV MSE in every printed digit on both checks.
