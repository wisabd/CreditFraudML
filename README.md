# CreditFraudML
Credit Fraud Detector


**Problem Statement**

With businesses moving online, fraud and abuse in online systems is constantly increasing as well. Traditionally, rule-based fraud detection systems are used to combat online fraud, but these rely on a static set of rules created by human experts. This project uses machine learning to create models for fraud detection that are dynamic, self-improving and maintainable. Importantly, they can scale with the online business.

**Data**

The example dataset used in this solution was originally released as part of a research collaboration of Worldline and the Machine Learning Group (http://mlg.ulb.ac.be) of ULB (Université Libre de Bruxelles) on big data mining and fraud detection.

The dataset contains credit card transactions from European cardholders in 2013. As is common in fraud detection, it is highly unbalanced, with 492 fraudulent transactions out of the 284,807 total transactions. The dataset contains only numerical features, because the original features have been transformed for confidentiality using PCA. As a result, the dataset contains 28 PCA components, and two features that haven't been transformed, Amount and Time. Amount refers to the transaction amount, and Time is the seconds elapsed between any transaction in the data and the first transaction.

More details on current and past projects on related topics are available on https://www.researchgate.net/project/Fraud-detection-5 and the page of the DefeatFraud project

We cite the following works:

Andrea Dal Pozzolo, Olivier Caelen, Reid A. Johnson and Gianluca Bontempi. Calibrating Probability with Undersampling for Unbalanced Classification. In Symposium on Computational Intelligence and Data Mining (CIDM), IEEE, 2015
Dal Pozzolo, Andrea; Caelen, Olivier; Le Borgne, Yann-Ael; Waterschoot, Serge; Bontempi, Gianluca. Learned lessons in credit card fraud detection from a practitioner perspective, Expert systems with applications,41,10,4915-4928,2014, Pergamon
Dal Pozzolo, Andrea; Boracchi, Giacomo; Caelen, Olivier; Alippi, Cesare; Bontempi, Gianluca. Credit card fraud detection: a realistic modeling and a novel learning strategy, IEEE transactions on neural networks and learning systems,29,8,3784-3797,2018,IEEE
Dal Pozzolo, Andrea Adaptive Machine learning for credit card fraud detection ULB MLG PhD thesis (supervised by G. Bontempi)
Carcillo, Fabrizio; Dal Pozzolo, Andrea; Le Borgne, Yann-Aël; Caelen, Olivier; Mazzer, Yannis; Bontempi, Gianluca. Scarff: a scalable framework for streaming credit card fraud detection with Spark, Information fusion,41, 182-194,2018,Elsevier
Carcillo, Fabrizio; Le Borgne, Yann-Aël; Caelen, Olivier; Bontempi, Gianluca. Streaming active learning strategies for real-life credit card fraud detection: assessment and visualization, International Journal of Data Science and Analytics, 5,4,285-300,2018,Springer International Publishing

**Preprocessing**

After the acquisition of the dataset, we import the libraries such as sklearn.preprocessing,
sklearn.decomposition, sklearn.manifold, etc to begin the preprocessing steps. The dataset is not
observed to have any missing values and the entire dataset is numerical hence there is no need
to encode the data. Since we are going to investgate distance-based models such as KNN, SVM
we perform feature scaling to ensure equal influence of every feature and avoid any biases due to
difference in scales. All features have been scaled already with the exception of amount and time.
For this, we import from sklearn.preprocessing the RobustScalar to to deal with the outliers in
the time, amount features as they have non-normally distributed values. It does so by eliminating
the median, scaling the data based on the interquartile range. The final preprocessing step is the train, test, validation split of the data which is done. StratifiedShuffleSplit is performed due to
imbalanced nature of the data. It ensures each fold maintains the same class distribution as the
original dataset by dividing data into 5 folds (4 for training, 1 for testing in each iteration). The
data is converted to NumPy arrays for compatibility with Sci-kit models. We then perform feature extraction using PCA and also remove outliers from features negatively correlated with the class label.
