# Novel Resilient Model Risk Forecasts based on Neuro Volatility Models

Recently, there has been a growing interest in using neuro volatility models in fuzzy forecasting and fuzzy option pricing. Neuro volatility models are used to model and predict financial market volatility by extending the neural network autoregressive (NNAR) model for nonlinear nonstationary time series data. In financial risk forecasting, various risk forecasting models for volatility are used to obtain the volatility forecasts, and the model risk ratio based on all the models is calculated to assess the stability of the financial system. However, the recently proposed neuro volatility models (based on neural networks such as LSTM, NNAR, etc.) are not used in evaluating the model risk. In this study, novel `neuro model risk forecasts' are obtained by including recently proposed neuro volatility models, and the resiliency of the financial system is studied.

The PDF copy of the paper can be downloaded from here: [Download Paper](https://ieeexplore.ieee.org/abstract/document/9918212) 

A preprint version of the paper is available in the repository.

Programming Language: [R](https://cran.r-project.org/bin/windows/base/) / [RStudio](https://posit.co/downloads/)

Data: The provided R codes download financial data directly from [Yahoo!Finance](https://ca.finance.yahoo.com/). The meteorological data used is available in the CSV file in the repository. The source of meteorological data is [Renewables.ninja](https://www.renewables.ninja/).

### Methodology

The novelty of this study is to obtain direct volatility forecasts using neural network models while taking basic time series models and autoregressive models into account. 
We introduce neuro model risk forecasts based on direct volatility forecasts, which allow more appropriate nonlinear nonstationary neuro volatility forecasting models. The work investigates the stability of the forecasts of different models, considering the proposed neuro model risk. Moreover, we investigate the models' performance in price forecasts using adjusted closing price data of Google, CBOE Volatility Index (VIX), and Bitcoin-USD.

When applying autoregression and machine learning models for time series data, a common approach is to evaluate the performance/accuracy of models by considering observed and forecast data. In this study, MAE, RMSE, and MAPE are used as measures of forecast errors.

#### Neuro Volatility Models

In finance, stock prices are modeled as a geometric Brownian motion, where the stock prices are denoted as $P_t$, $t = 1, \ldots, T$. 
The first step when modeling volatility is to transform the adjusted closing prices $P_t$ and calculate the log returns. Then, calculate the mean of the log returns, denoted $\bar{r}$. 
We will then compute the correlation between $r_t-\bar{r}$ and $sign(r_t-\bar{r})$ denoted as $\hat{\rho} = corr(r_t-\bar{r}, sign(r_t-\bar{r}))$, then compute the observed volatility $V_t = |r_t-\bar{r}|/\hat{\rho}$. The observed volatility formula stems from the unbiased estimator of the standard deviation.
The observed volatility can then be used as the input time series to fit the neural network model; the fitted neural network model with the volatility series as the training data can forecast future volatility of the stock/cryptocurrency prices.

The Figure below provides a general representation of a neural network with one hidden layer. The network forecasts volatility at time $t+1,$ $V_{t+1},$ using lag values of observed volatility ($V_{t}, V_{t-1}, \ldots , V_{t-p}$).

<img src="Images/NeuroVolatilityModel.png" alt="Neuro Volatility Model" width="500"/>




