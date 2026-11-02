# econ3916-lab12-ols-prediction
# OLS as a Line of Best Fit: Estimation versus Prediction

## Objective

I used ordinary least squares to show the difference between estimating a relationship (a coefficient and its uncertainty) and predicting new outcomes (error on data the model has not seen).

## Methodology

- I fitted the same simple OLS line three ways: with the closed-form formula, with statsmodels, and with scikit-learn. All three gave the same intercept and slope.
- I added up to 100 columns of pure noise to a regression and tracked R-squared and adjusted R-squared as each batch of noise went in.
- I split the data into training and test sets before fitting anything, then scored an eight-feature model on the rows it was fitted to and on test rows it never saw.
- I used one model specification for two separate jobs: reading off the AveRooms coefficient with its 95% confidence interval, and measuring test RMSE.
- I wrote a small function, `holdout_rmse()`, that takes any list of predictors and scores the resulting model on the same test rows, so different feature sets can be compared fairly. I used it on median income alone.
- (Challenge) I refit the model after dropping the districts at the 5.0 ceiling.

## Key Findings

- **Same line, three tools:** The closed form, statsmodels and scikit-learn all gave a slope of [YOUR VALUE].
- **R-squared rewards noise:** R-squared was [YOUR VALUE] with no noise columns and [YOUR VALUE] with 100 noise columns. It went up every time I added noise, even though the noise carries no information. Adjusted R-squared did not rise the same way, because it penalizes extra predictors.
- **Training error flatters the model:** The eight-feature model had a train RMSE of [YOUR VALUE] and a test RMSE of [YOUR VALUE]. The test number is the honest measure of how well it predicts.
- **Estimation and prediction answer different questions:** From the same specification, the AveRooms coefficient was [YOUR VALUE] with a 95% CI of [YOUR VALUE], and the model's test RMSE told me separately how well it predicts. A model can be useful for one job and not the other.
- **One predictor as a baseline:** Using median income alone, `holdout_rmse()` gave a test RMSE of [YOUR VALUE].
- **(Challenge) Capped districts:** Dropping the districts at the 5.0 ceiling: [YOUR RESULT].
