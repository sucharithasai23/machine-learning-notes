## Machine Learning 
ml-project-checklist

This checklist can guide you through your Machine Learning projects. There are eight main steps:

1. Frame the problem and look at the big picture.
2. Get the data.
3. Explore the data to gain insights.
4. Prepare the data to better expose the underlying data patterns to Machine Learning algorithms.
5. Explore many different models and short-list the best ones.
6. Fine-tune your models and combine them into a great solution.
7. Present your solution.
8. Launch, monitor, and maintain your system.
9. Obviously, you should feel free to adapt this checklist to your needs.

## Frame the problem and look at the big picture
Define the objective in business terms.
How will your solution be used?
What are the current solutions/workarounds (if any)?
How should you frame this problem (supervised/unsupervised, online/offline, etc.)
How should performance be measured?
Is the performance measure aligned with the business objective?
What would be the minimum performance needed to reach the business objective?
What are comparable problems? Can you reuse experience or tools?
Is human expertise available?
How would you solve the problem manually?
List the assumptions you or others have made so far.
Verify assumptions if possible.

## Get the data
Note: automate as much as possible so you can easily get fresh data.

List the data you need and how much you need.
Find and document where you can get that data.
Check how much space it will take.
Check legal obligations, and get the authorization if necessary.
Get access authorizations.
Create a workspace (with enough storage space).
Get the data.
Convert the data to a format you can easily manipulate (without changing the data itself).
Ensure sensitive information is deleted or protected (e.g., anonymized).
Check the size and type of data (time series, sample, geographical, etc.).
Sample a test set, put it aside, and never look at it (no data snooping!).

## Explore the data

Note: try to get insights from a field expert for these steps.

Create a copy of the data for exploration (sampling it down to a manageable size if necessary).
Create a Jupyter notebook to keep record of your data exploration.
Study each attribute and its characteristics:
Name
Type (categorical, int/float, bounded/unbounded, text, structured, etc.)
% of missing values
Noisiness and type of noise (stochastic, outliers, rounding errors, etc.)
Possibly useful for the task?
Type of distribution (Gaussian, uniform, logarithmic, etc.)
For supervised learning tasks, identify the target attribute(s).
Visualize the data.
Study the correlations between attributes.
Study how you would solve the problem manually.
Identify the promising transformations you may want to apply.
Identify extra data that would be useful (go back to "Get the Data" on page 502).
Document what you have learned.

## Prepare the data
Notes:

Work on copies of the data (keep the original dataset intact).
Write functions for all data transformations you apply, for five reasons:
So you can easily prepare the data the next time you get a fresh dataset
So you can apply these transformations in future projects
To clean and prepare the test set
To clean and prepare new data instances
To make it easy to treat your preparation choices as hyperparameters
Data cleaning:
Fix or remove outliers (optional).
Fill in missing values (e.g., with zero, mean, median...) or drop their rows (or columns).
Feature selection (optional):
Drop the attributes that provide no useful information for the task.
Feature engineering, where appropriate:
Discretize continuous features.
Decompose features (e.g., categorical, date/time, etc.).
Add promising transformations of features (e.g., log(x), sqrt(x), x^2, etc.).
Aggregate features into promising new features.
Feature scaling: standardize or normalize features.

## Short-list promising models
Notes:

If the data is huge, you may want to sample smaller training sets so you can train many different models in a reasonable time (be aware that this penalizes complex models such as large neural nets or Random Forests).
Once again, try to automate these steps as much as possible.
Train many quick and dirty models from different categories (e.g., linear, naive, Bayes, SVM, Random Forests, neural net, etc.) using standard parameters.
Measure and compare their performance.
For each model, use N-fold cross-validation and compute the mean and standard deviation of their performance.
Analyze the most significant variables for each algorithm.
Analyze the types of errors the models make.
What data would a human have used to avoid these errors?
Have a quick round of feature selection and engineering.
Have one or two more quick iterations of the five previous steps.
Short-list the top three to five most promising models, preferring models that make different types of errors.

## Fine-Tune the System
Notes:

You will want to use as much data as possible for this step, especially as you move toward the end of fine-tuning.
As always automate what you can.
Fine-tune the hyperparameters using cross-validation.
Treat your data transformation choices as hyperparameters, especially when you are not sure about them (e.g., should I replace missing values with zero or the median value? Or just drop the rows?).
Unless there are very few hyperparameter values to explore, prefer random search over grid search. If training is very long, you may prefer a Bayesian optimization approach (e.g., using a Gaussian process priors, as described by Jasper Snoek, Hugo Larochelle, and Ryan Adams (https://goo.gl/PEFfGr))
Try Ensemble methods. Combining your best models will often perform better than running them individually.
Once you are confident about your final model, measure its performance on the test set to estimate the generalization error.
Don't tweak your model after measuring the generalization error: you would just start overfitting the test set.

## Present your solution
Document what you have done.
Create a nice presentation.
Make sure you highlight the big picture first.
Explain why your solution achieves the business objective.
Don't forget to present interesting points you noticed along the way.
Describe what worked and what did not.
List your assumptions and your system's limitations.
Ensure your key findings are communicated through beautiful visualizations or easy-to-remember statements (e.g., "the median income is the number-one predictor of housing prices").
## Launch!
Get your solution ready for production (plug into production data inputs, write unit tests, etc.).
Write monitoring code to check your system's live performance at regular intervals and trigger alerts when it drops.
Beware of slow degradation too: models tend to "rot" as data evolves.
Measuring performance may require a human pipeline (e.g., via a crowdsourcing service).
Also monitor your inputs' quality (e.g., a malfunctioning sensor sending random values, or another team's output becoming stale). This is particularly important for online learning systems.
Retrain your models on a regular basis on fresh data (automate as much as possible).