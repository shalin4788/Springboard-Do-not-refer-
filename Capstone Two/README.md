https://www.kaggle.com/c/quora-insincere-questions-classification

# Project Organization

├── LICENSE
├── README.md          <- The top-level README for developers using this project.
│
├── data
│   ├── interim        <- Intermediate data that has been transformed.
│       └── train.csv
│       └── test.csv
│   ├── processed      <- The final, canonical data sets for modeling.
│       └── FeatureEngineering_tfidf_Train.csv
│       └──FeatureEngineering_tfidf_Test.csv
│   └── raw            <- The original, immutable data dump.
│       └── train.csv
│       └── test.csv
│
├── notebooks          <- Jupyter notebooks. Naming convention is a number (for ordering),
│   ├── 1. Quora Insincere Capstone Data Wrangling.ipynb
│   ├── 2. EDA_Quora Insincere Capstone Data.ipynb
│   ├── 3. Preprocessing and Training Data Development.ipynb
│   └── 4. Quora Insincere Classification - Modeling Step.ipynb 
│
├── reports            <- Generated analysis as HTML, PDF, LaTeX, etc.
│   ├── Final_Rep_Quora_Insincere_Classification.docx
│   └── TBD
│                      
└── src                <- Source code for use in this project.
    └── figures        <- Scripts to download or generate figures
    └── models         <- Scripts to download or generate model generated for future test data prediction

Project based on the cookiecutter data science project template. #cookiecutterdatascience

# Description

**Problem**
An existential problem for any major website today is how to handle toxic and divisive content. Quora wants to tackle this problem head-on to keep their platform a place where users can feel safe sharing their knowledge with the world.

**Tasks**
- Perform Data Wrangling on the merged traiing and test dataframe
    - Data Collection
    - Data Organization
    - Data Definition
    - Data Cleaning  
-	Develop scalable methods to detect toxic and misleading content like:
    - Non neutral tone
    - Disparaging tone
    - False information
    - Absurd assumptions
    - Sexual content
-	Weed out insincere questions -- those founded upon false premises, or that intend to make a statement rather than look for helpful answers.

**Data used**
Data files contain
-	Training and testing data set where training data set contains quora questionId’s with insincere content marked by value = 1, otherwise 0
-	Number of word embeddings along with the dataset that can be used in the models
The file is a matrix of about 376 thousand observations and 7 variables.

**Steps performed**
- **Data Wrangling** - Extraction, cleaning of text data by removing punctuations, NaN, used functions like Stemming, Tokenization, Vectorization etc.
- **Exploratory Data Analysis (EDA)** -  for seeing co-relation of features in the Quora data set, created unigrams, bigrams, word cloud and 3d scatter plots for this purpose
- **Feature Engineering** (Pre-processing and training data development) - Performed numeric variable scaling, TFIDF vectorization to generate categorical variables as features to generate an updated feature engineered dataset. Thereafter broke the dataset into training and test data set
        - After the above steps, the data was condensed into 102K observations which is further broken down into training and testing data set containing 506 features created by count vectorization of 'question_text' column
- **Modeling**  - See details below

As a part of modeling step,

**Models applied**
This is a classification problem, in supervised learning. Here I have applied the following classification models:
- Logistic Regression
       - Norma
       - With L2 regularization
- Naive Bayes
- Decision Trees
- Random Forest
- Gradient Boost

**Model Evaluation**
- Used metrics like Precision, Accuracy, Recall, f1 score, ROC AUC score to evaluate model performance
- Built confusion matrix to see false positives and false negatives after running each model against the training dataset and computing predictions against validation dataset
- f1 weighted score and ROC AUC score were used for shortlisting best performing models

- Additionally, hyperparameter tuning was done on the best performing shortlisted model(s) to enhance performance.
- Also, Cross validation using Grid search was applied to pick up random pairs of training and validation data by splitting the training set into k smaller sets, where a model is trained using k-1 of the folds as training data and the model is validated on the remaining part.
- Eventually, model was saved for future application

**Unseen test data prediction**
Saved model was applied on the unseen test dataset, fitted and prediction done, scores measured to evaluate how efficient the model was.

## References

https://medium.com/@datamonsters/text-preprocessing-in-python-steps-tools-and-examples-bf025f872908

https://www.geeksforgeeks.org/python-longest-string-in-list/

https://stackoverflow.com/questions/33047818/remove-punctuation-for-each-row-in-a-pandas-data-frame?noredirect=1&lq=1

https://stackoverflow.com/questions/1801668/convert-a-python-list-with-strings-all-to-lowercase-or-uppercase

https://stackoverflow.com/questions/3849509/how-to-remove-n-from-a-list-element

https://stackoverflow.com/questions/29523254/python-remove-stop-words-from-pandas-dataframe

https://stackoverflow.com/questions/48617589/beginner-stemming-in-pandas-produces-letters-not-stems

https://stackoverflow.com/questions/49984905/count-number-of-words-per-row

https://stackoverflow.com/questions/56563681/remove-the-rows-from-pandas-dataframe-that-has-sentences-longer-than-certain-wo

https://stackoverflow.com/questions/62918301/return-rows-w-string-content-that-dont-have-words-exceeding-a-certain-max-leng

https://stackoverflow.com/questions/15411158/pandas-countdistinct-equivalent

https://scikit-learn.org/stable/modules/generated/sklearn.feature_extraction.text.CountVectorizer.html

https://medium.com/@dudsdu/an-example-of-word-cloud-with-mask-4cbbd699fb14

https://discuss.python.org/t/countvectorizer-throwing-valueerror-empty-vocabulary-perhaps-the-documents-only-contain-stop-words/5388/2

https://stackoverflow.com/questions/23939750/understanding-max-features-parameter-in-randomforestregressor

https://stackoverflow.com/questions/20662023/save-python-random-forest-model-to-file
