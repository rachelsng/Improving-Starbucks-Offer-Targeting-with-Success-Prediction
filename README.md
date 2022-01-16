# Improving Starbucks Offer Targeting with Redemption Prediction



## Context
This simulated Starbucks Rewards App dataset was a capstone project option by Udacity Data Scientist Nanodegree with an open-ended problem statement to derive business value for Starbucks. 

Here, it is used to build a model that can better rank which offers to serve to each customer. We aim to address the twin problems of:

1. <b>Wastage</b> - Customers are sent (and therefore use) offers even though they would made a purchase without one
2. <b>Irrelevance</b> - Irrelevant offers are sent which customers tune out, leading to missed conversion opportunities


## Objective
- Understand current offer redemption trends and highlight improvement areas
    - See *02_Exploratory_Data_Analysis.ipynb*
- Build a framework to rank offers to serve to customers by:
    - Tuning and select a classifier that predicts redemption
    - Tuning and selecting a regressor that predicts expected spend if redeemed 
    - Combine both to output an understandable ranking of offers
    - See *03_Redemption_and_Expected_Spend_Prediction.ipynb*


## Dataset
This dataset is available from Kaggle (https://www.kaggle.com/ihormuliar/starbucks-customer-data). Data is simulated but closely mimics customer behavior over the Starbucks Rewards App. 

It consists of 3 csv files:

1. *portfolio.csv*: 10 entries with offer configuration information
2. *profile.csv*: 17,000 entries with customer demographic information
3. *transcript.csv*: 306,534 rows of 4 types of interactions; offer received, offer viewed, offer success and transactions

## Exploratory Data Analysis Highlights
- <b>Success Rate</b>: Only about 42% of all promotions sent out are ultimately redeemed on purpose ("success").
- <b>Wastage</b>: 13% of customers do not even see the promotion and yet redeemed it suggesting that the promotion was unnecessary and value was lost
- <b>Frequency</b>: Customers received on average 4 offers a month of varying configurations
- Offer Success differs most significantly by
    - <b>Gender</b>: There is higher success with females compared to males
    - <b>Duration of being a member</b>: Long term members (>500 days) have higher success
    - <b>Social Media</b>: There is higher success if the offer is on social media as well
- Spending differs most significantly by:
    - <b>Age</b>: Older individuals spend more
    - <b>Income</b>: High-income individuals spend more

*Packages used: pandas, numpy, matplotlib, seaborn*

## Model Building Approach

<b>Predict Offer Success</b>
- 4 classifiers were tuned and trained (Logistic Regression, Support Vector Machine, Random Forest, XGBoost)
- XGBoost had the best performance, with 73% precision (this is a <b>significant improvement</b> from the 42% business success rate above)

<b>Predict Expected Spend</b>
- 3 regressors were tuned and trained (Linear Regression, Random Forest, K-Nearest Neighbours)
- Random Forest had the best performance, with 0.5 r-squared.

<b>Offer Ranking</b>
1. Demographic and promotions data first fed into the classifier to get *P(Offer Success)*
2. The same features are then fed to the regressor to get *Expected Spend*
3. The promotions are then ranked by *P(Offer Success) * 𝐸𝑥𝑝𝑒𝑐𝑡𝑒𝑑𝑆𝑝𝑒𝑛𝑑*

*Packages used: sklearn, xgboost*

## Files
- *01_Data_Preprocessing.ipynb*: Data formatting, filtering and grouping
- *02_Exploratory_Data_Analysis.ipynb*: 
- *03_Redemption_and_Expected_Spend_Prediction.ipynb*: Classifier & regressor tuning, selection & combined expected value framework
- *data*: 3 original CSV files, 1 preprocessed CSV file and 1 example to demonstrate model application
- *images*: Supporting images

## Credits

![](./images/coffee.jpg)
*Photo by Fahmi Fakhrudin from Unsplash*