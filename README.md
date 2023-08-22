# Stock Price Prediction
## Project Overview
Investment firms, hedge funds and even individuals have been using financial models to understand market behaviour better and make profitable investments and trades. A wealth of information is available in the form of historical stock prices and company performance data, suitable for machine learning algorithms to process.

Can we predict stock prices with machine learning? Investors make educated guesses by analyzing data. They will read the news, study the company history, industry trends, and other data points that go into making a prediction. The prevailing theories are that stock prices are totally random and unpredictable, raising the question of why top firms like Morgan Stanley and Citigroup hire quantitative analysts to build predictive models. We have this idea of the trading floor being filled with adrenaline infuse men with loose ties running around yelling something into a phone. However, these days we are more likely to see rows of machine learning experts quietly sitting in front of computer screens. About 70% of all orders on Wall Street are now placed by software. We are now living in the age of algorithms.

This project utilizes the ARIMA model for base predictions and then built a Deep Learning model to improve it further. Stock prices are predicted for Tech Giants like Apple, Google, Tesla, Microsoft and Amazon.
## Dataset
Webscraped https://in.finance.yahoo.com using selenium and BeautifulSoup.
## Deep Learning Model
We train the model using the training dataset records and then use it to forecast the following week’s closing values (i.e., the next five values as a week consists of five working days). The forecasting is done in a multi-step manner with a walk-forward validation mode. <br>
The details of the design of each layer and the overall architecture of the model are as follows :
<br>
The input data’s shape to the network’s input layer is (5, 1), indicating that the previous five values (i.e., one week’s data) of the time series are used as the input. Only one attribute of the data (i.e., the closing value) is considered. The input layer passes the data onto the LSTM layer with 200 nodes at the output, with the Leaky ReLU activation function is used in these nodes. The LSTM layer’s output is passed to another LSTM layer with 200 nodes at the output, with the Leaky ReLU as an activation function. This layer’s output is then passed onto a dense layer with 200 nodes at its input and output, with Leaky ReLU activation. This layer’s output is passed onto another dense layer with 200 nodes at its input and 100 nodes with a Leaky ReLU activation function at the output. This layer’s output is passed onto another dense layer with 100 nodes at its input and 50 nodes with a Leaky ReLU activation function at the output. The dense layer is finally connected to the output layer that is also fully-connected. The output layer has 50 nodes at its input and 5 nodes at the output. The 5 nodes at the output produce the forecasted values for the five days of the following week. Again the output layer uses Leaky ReLU as an activation function. The model uses MSE as the loss function and ADAM as the optimizer with a custom learning rate. 
## Results
|           | ARIMA Model (RMSE) | Deep Learning Model (RMSE) | 
| --------- | ------------------ | -------------------------- |
| Apple     | 6.40               | 4.82                       |
| Tesla     | 108.11             | 66.40                      |
| Google    | 210.40             | 115.66                     |
| Microsoft | 7.26               | 6.23                       |
| Amazon    | 113.18             | 87.48                      |
