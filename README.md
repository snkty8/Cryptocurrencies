# Cryptocurrencies

## Overview 
Accountability Accounting, a prominent investment bank, is interested in offering a new cryptocurrency investment portfolio for its customers.  However, the company is not well versed in the world of cryptocurrencies.  They have asked us to create a report that includes what cryptocurrencies are on the trading market and how they could be grouped to create a classification system for this new investment. The data we will be working we is not ideal, and will need to be processed to fit the machine learning models. There is no known output.  This is the perfect situation for unsupervised learning. 

## Results

The was retrieved from [CryptoCompare](https://min-api.cryptocompare.com/data/all/coinlist)
1. The data for preprocessed for PCA
    - Rows that had at least one null value were removed. The CoinName column was also removed since it was not going to used on the clustering algorithim. The get_dummies method was used to create variable for the two text features, Algorithim and ProofType. Then the StandardScaler fit_transfrom functin was used to standardize the features. Below is a screenshot of the processed dataframe:

    ![image](https://github.com/snkty8/Cryptocurrencies/blob/main/images/crypto_data_df.png)

2. Data dimensions were reduced using PCA:
    - PCA was applied, and a new dataframe was created. It included the following columns: PC1, PC2, and PC3.  Below is a screen shot of the dataframe:

    ![image](https://github.com/snkty8/Cryptocurrencies/blob/main/images/pcs_df.png)

3. Clustering Cryptocurrencies Using K-Means:
    - An elbow curve was created using data from the pcs dataframe.  The elbow curve shows the bests value for K is 4.  Below is a screen show of the elbow curve:

    ![image](https://github.com/snkty8/Cryptocurrencies/blob/main/images/elbow_curve.png)

    - The pcs dataframe was also used to make predictions. A new dataframe was created, clustered_df, by concatenating the crypto_data_df and pcs_df dataframe on the same columns. Columns CoinNames and Class, this column held the predictions.  Below is a screen shot of the clustered_df dataframe: 

    ![image](https://github.com/snkty8/Cryptocurrencies/blob/main/images/clustered_df.png)

4.  Visualizing Cryptocurrencies:
    - A 3D scatter plot was created to plot the three clusters from the clustered_df dataframe.  Below is a screen shot of the plot:

    ![image](https://github.com/snkty8/Cryptocurrencies/blob/main/images/3D_Scatter.png)

    - A table with tradable cryptocurrencies was created: 

    ![image](https://github.com/snkty8/Cryptocurrencies/blob/main/images/tradable_crypto.png)

    - A dataframe showing TotalCoinSupply, TotalCoinsMined, CoinName, and Class:

    ![image](https://github.com/snkty8/Cryptocurrencies/blob/main/images/plot_df.png)

    - Lastly, using hvplot a scatter plot of TotalCoinsMined vs TotalCoinSupply ordered by Class was also created. 

    ![image](https://github.com/snkty8/Cryptocurrencies/blob/main/images/hvplot.png)   

## Summary 

Using unsupervised learning we were able to successfully indentify 533 tradable cryptocurrencies.  Further analysis would need to be done to figure out how profitable each of these currencies are on the market. 
