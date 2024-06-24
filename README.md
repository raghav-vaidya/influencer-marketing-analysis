# Influencer Marketing Analysis

The learning objectives for this assignment are to learn ways to\
(i)	Detect social “influencers” using network analytics
(ii)	Quantify the financial value of influence
(iii) Identify and leverage influencers 
The assignment has two parts: I and II. In Part I, you will use training data on social influence to build a model predicting influencers, to find out the important predictors of influence, and to quantify the financial value of influence. In Part II, you will collect tweets, and use the predictors from Part I to identify 20 top influencers in a domain of your choice. 

Part I: Find predictors of influence
The dataset for Part I can be found at http://www.kaggle.com/c/predict-who-is-more-influential-in-a-social-network
Use the training dataset only to build and validate your model. Each observation in the dataset describes two individuals, A and B. There are 11 variables for each person based on Twitter activity, e.g., number of followers, retweets, network characteristics, etc. Each observation shows whether A > B (Choice = “1”) or B > A (Choice = “0”). 

Using the training data set (train.csv), create an analytic model for pairs of individuals to classify who is more influential
	Check if you should use all variables
	A transformation of the variables (like A/B or A-B) may be better than using A and B variables separately, and may also be easier to interpret. 
	Normalize all data so that all values are between 0 and 1
	Report the confusion matrix of your “best” model (provide screenshot)
From your model, which factors are best predictors of influence? You can use a logistic regression for this part and provide screenshots. How can a business use your model/results? 


Calculate the financial value of your model
A retailer wants influencers to tweet its promotion for a product. If a non-influencer tweets, there is no benefit to the retailer. If an influencer tweets once, there is a 0.01% chance that his/her followers will buy one unit of a product. Assume the retailer has a profit margin of $10 per unit, and that one customer can buy only one unit. If an influencer tweets twice, the overall buying probability will be 0.015%. Without analytics, the retailer offers $5 to each person (A and B) to tweet once. With analytics, the retailer offers $10 to those identified as influencers by the model to send two tweets each. If the model classifies an individual as a non-influencer, s/he is not selected/paid by the retailer to tweet.

What is the lift in expected net profit from using your analytic model (versus not using analytics)? Show all calculations. What is the lift in net profit from using a perfect analytic model (versus not using analytics)?
Assumption: Each user appears only once in the data
A	B	Choice (A>B?)
John	Ted	Yes
Sue	Ron	Yes
Fred	Sandy	No (Sandy > Fred)
Alex	Moe	No (Mo > Alex)

The Influencers in the above table are John, Sue, Sandy & Moe, but no ordered ranking is possible (or needed in this case). 


Part II: Finding influencers from Twitter

A sample of tweets and related information is shown in tweets_sample.csv.

Write a script that parses through the tweets and does the following: For each tweet:

Any retweet (RT), mention or reply should result in an arrow from the person retweeting to the person retweeted, mentioned or replied to. However, you don’t need to draw the actual arrows and the network. Instead, create a three-column .CSV file as follows: If @XYZ retweets a tweet by @ABC, then put the following in the .CSV file:

Column 1 	Column 2	Column 3 (type of content)
@ABC		@ABC		Tweet (self-loop)
@XYZ		@ABC		RT

Most social network analysis tools (e.g., NodeXL, Gephi or UCINet) will take the first two columns and draw arrows from the user in the left column to the one in the right – You can also use Networkx in Python to draw networks. Note that in most cases the set of tweets you may fetch will not have the original tweet that is being retweeted by someone else. E.g., a tweet in your data (tweeted by, say, @XYZ) may be:  “RT @ABC Working on my social media assignment.” 

It is quite possible that you will not have the original tweet by @ABC in your data. Still an arrow should go from @XYZ to @ABC. Therefore, even if you have fetched 5000 tweets by 5000 unique users, your network may consist of a much larger set of users.

Calculate the degree, betweenness and closeness of each node in the above network. 

Using the results from Part I, create a list of top 20 influencers from the tweets. Here is one way to do it. 

You can use the coefficients from the model in Part I as weights for the variables in creating an influence score for each user.  You should normalize your data before creating the overall scores.  Note that the Kaggle data doesn’t show what each network characteristic means. However, generally such metrics are presented in the following sequence: Degree, betweenness and closeness. Also, as I have already stated,  not all factors found to be important from the first part may be available in the data you collect from Twitter.
![image](https://github.com/raghav-vaidya/influencer-marketing-analysis/assets/142241574/4a470572-7c00-4b3c-9521-9e66ac7c1325)
