# CTML_Model

# Overview
## CTML Take-Home Test
# Business Objective & Challenge
## 1: Breast Cancer Dataset EDA
The “wdbc” data-set you will be working with can be downloaded from here.
Please produce a well-presented Jupyter notebook – including any visualisations you feel are useful – which addresses the following:

 a.	What are the mean, median and standard deviation of the “perimeter” feature?

b.	Is the first feature in this data set (the “radius”) normally distributed? Quantify your answer. If not, what might be a more appropriate distribution?

c.	Train a classifier to predict the diagnosis of malignant or benign. Compare the results of two classifiers e.g. SVM, logistic regression, decision tree etc.

# ML Development Process
## Data Reading
### Attribute Information:

5. Number of instances: 569 

6. Number of attributes: 32 (ID, diagnosis, 30 real-valued input features)

7. Attribute information

1) ID number
2) Diagnosis (M = malignant, B = benign)
3-32)

Ten real-valued features are computed for each cell nucleus:

	a) radius (mean of distances from center to points on the perimeter)
	b) texture (standard deviation of gray-scale values)
	c) perimeter
	d) area
	e) smoothness (local variation in radius lengths)
	f) compactness (perimeter^2 / area - 1.0)
	g) concavity (severity of concave portions of the contour)
	h) concave points (number of concave portions of the contour)
	i) symmetry 
	j) fractal dimension ("coastline approximation" - 1)

Several of the papers listed above contain detailed descriptions of
how these features are computed. 

The mean, standard error, and "worst" or largest (mean of the three
largest values) of these features were computed for each image,
resulting in 30 features.  For instance, field 3 is Mean Radius, field
13 is Radius SE, field 23 is Worst Radius.

All feature values are recoded with four significant digits.

8. Missing attribute values: none

9. Class distribution: 357 benign, 212 malignant

## Data Quality
## Summarizing Missing Values

# Data Exploration and Data Preparation
##   In this section the dataset will be analyzed to come up with the main characteristics that could help to understand the nature of the data. The analysis will assist to find out which features are more crucial in predicting whether a sample is cancerous or not.
## Descriptive Statistics
### Descriptive Statistics for Continuous variable

# Challenge 1 What are the mean, median and standard deviation of the “perimeter” feature?

# Challenge 2 Is the first feature in this data set (the “radius”) normally distributed? Quantify your answer. If not, what might be a more appropriate distribution?

#  Categorical Variable (Target Variable)

## Mean Features Plot
There are a few things to point out on this plot.

From all histograms in the diagonal plots of the grid, only the fractal dimension has no visible effect on the square of the tumor. This is also seen in all the plots of the last row / column. This is convenient because the fractal dimension is the unexplained oblique feature that we have just talked about. This latter is a strong candidate for feature selection. The second lowest visual effect (I am saying visual because we will see some numbers later) is on symmetry. All other characteristics have a significant effect on the classification of tumors and the scatterplots look quite 'separable'. We can also see some 'beautiful plots' on the respective geometric features radius, area, and circumference, which are to be expected. This high correlation between features can be a problem for few ML algorithms.

## Error Features Plot

We didn't expect to find anything here - and most feature errors have no effect - but look at radius ,perimeter , area  and compactness. The data suggest that the greater the error in these characteristics, the greater the likelihood of malignant tumors. How can we explain it?

Let us remember how standard error is calculated: by dividing the standard deviation by the square root of the sample size.

SE = σ / n
 
I will assume that the sample size does not change for each tumor sample, so the variance of the standard error is only due to the standard deviation.

Assuming that this is the case, we can interpret that there is a high irregularity on the geometry of the malignant tumor, which causes a high standard deviation!

## Worst Features Plot
These plots are very similar to the previous ones. This should be expected because the worst features are sub-samples of average data. Only by looking at those scenes is it difficult to say which is more important for the prediction model. We need to get some numbers to see if there is a significant difference.

# Correlations
To calculate the correlations we can use the pandas corr method.

To visualize it better we can use the classic seaborn's heatmap - which is perfectly fine - but I will plot it using horizontal bar charts.

The downside of not plotting a heatmap is that we do not see how features are correlated to each other: there might be redundant features we don't need to feed a machine learning model. We can already see highly correlated features from our previous plots (e.g. Perimeter and Area), but I've chosen to keep them all and let the algorithms decide for them selves which ones are important and which ones aren't (feature selection and regularization).

## Correlation by Feature Type
First, lets see if we can find a predominant type of feature (worst, mean or se). Did we visualize it correctly in the previous plots?

# Feature engineering
## We are Creating a Volume Mean Feature using radius_mean

## Feature Scaling

Since the range of values of raw data varies widely, in some machine learning algorithms, objective functions will not work properly without normalization. For example, the majority of classifiers calculate the distance between two points by the Euclidean distance. If one of the features has a broad range of values, the distance will be governed by this particular feature. Therefore, the range of all features should be normalized so that each feature contributes approximately proportionately to the final distance.

## Features Distribution

# Model development
# Data Partition :Splitting the Data for training and testing
# Imbalanced Learning
# Feature Selection using Recursive feature elimination (RFE)
Feature selection works by selecting the best features based on univariate statistical tests. It can be seen as a preprocessing step to an estimator. SelectKBest removes all but the k highest scoring features

# Classification Model
we are going to build a classification model and evaluate its performance using the training set.

## Baseline Model 
### We are using Logistic regression , Support vector machine and Decision tree technique to train a classifier to predict the diagnosis of malignant or benign. 
### case 1 : select all Features
### case 2 : Select feaures based on Recursive feature elimination (RFE) with random forest
### Bayesian Optimization Hyperparameter Tuning

### Final Model with feature selection and Hypertunning
### Logistic Regression Model
### SVM Model
### Decision Tree Classifier
# Challenge #3: Spearman’s Footrule Distance
