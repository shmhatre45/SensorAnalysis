# SensorAnalysis
Linear regression model to estimate the traffic volume at each sensor location

Information about the data:

The primary sources of the data for this study are traffic counts from the traffic survey group of the NC Department of Transportation (DOT).
We requested the six coastal district’s traffic volume data for Hurricane Florence and Hurricane Dorian. from 9/5/2018-19 to 9/20/2018-19. 
The data's request is made to cover traffic volume one week before hurricane landfall, one week during hurricane landfall, and one week after the hurricane landfall. 
In the current study, we analyze the Hurricane Florence (2018) traffic volume data during a hurricane evacuation, i.e., five days before the hurricane landfall at the NC coastline.
The traffic volume data of six coastal districts cover forty-two counties of NC State.
The data was provided for thirty-eight sensor locations, consisting of one excel file for each sensor location.
Each excel file contains the sensor location county, route number, lane direction, district number, and hourly traffic volume data with dates.

Data for Analysis:

The input data for the predictive analysis is retrieved from the traffic count data received from NCDOT in the following steps:
Initially, received data is separated district wise for each hurricane in the excel.
Finally, the predictive analysis's required input data is prepared using different data exploration and data cleaning techniques in python.
After analyzing the predictive analysis results, the sensor association analysis is performed.

Methodology

The linear regression is used for estimating the traffic count at each sensor location. 
The dependent variable (DV) for the linear regression is hourly traffic volume at the sensor location.
The independent variables (IVs) for the linear regression consist of traffic volume at sensor location before 1 hr, 2 hr, 3hr, 4 hr and traffic volume at 
other sensor location before 1hr, 2hr, 3hr, and 4hr. 

[1] In the statistical analysis, after preparing the input data and cleaning the data by omitting the data with missing value, if the feature variable (IV) is greater than five, 
then the feature selection step is performed. 

[2] In this analysis, we use the ‘backward elimination’ method to select the most significant features. As the name suggests, we need to feed all the possible features 
to the model at first.We check the model's performance then iteratively remove the worst performing feature one by one until the model's overall performance comes in an acceptable range. 
The performance metric used here to evaluate the feature performance is a p-value. If the p-value is above 0.05, then we remove the feature; else, we keep it.

[3] Next, we perform the linear regression and test the ‘goodness of fit’ using the Normal QQ-plot of the residual and three different normality test. 
The three various normality tests are the Shapiro-Wilk test, D’Angostino and Pearson’s test, and the Anderson-Darling test. 
If the model passes these tests, we stop and accept the data; otherwise, we do the outlier detection analysis. 
We calculate the Cook’s distance (CD) to identify the most influential observation in outlier detection. 

[4] In this analysis, we drop the observation with CD > (4/n) where ‘n’ is the total number of the observations. 
After dropping the observations, we fit the model with data and again check for ‘goodness of fit. If it passes the normality tests, we stop and accept the data.

[5] Repeating the procedure for all the selected sensor location, we get the data in the format, which is sensor location and features 
(sensor locations predicting the traffic at that particular location). 

