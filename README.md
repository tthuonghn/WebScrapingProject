# WebScrapingProject
## webscraping.py
Crawl IMDB list of Most popular by Genre (http://www.imdb.com/genre/?ref_=nv_ch_gr_3).
  - Call getMovieTitlesByGenres(<genre>, <no. of movie>) to get a <list of movie ids>
  - Call getMovieAttributes(<list of movie ids>) to get a list of Movie object including movie attributes(title, rating, datePublished, year, directors...). Each movie contains a list of Review object including review attributes(title, author, date, rating, useful rating, content...)
  - Save in JSON format

## loadReviews.py
Common functions to load json file, process text and generate training & test set
  - loadReviews(<filename>): load json file saved by webscraping.py, return list of ONLY reviews and review attributes
  - textProcessing(<reviews>, <removeStopwords>, <minLength>): remove all numbers by default. remove stop words and set min length based on user input (purpose: to test effects of these text processing on final model)
  - generateTrainingTestSet(<reviews>, <combineTitle>): split data in training and test set (75/25). Option to combine or not combine review title (purpose: to test effects of these text processing on final model)

## nltk
## NaiveBayesClassifier.py
## NaiveBayesClassifier-ngram.py
Run NB algorithm to classify reviews into "positive" and "negative"
  - Call loadReviews
  - Call textProcessing
  - Call generateTrainingTestSet
  - Call unigramNaiveBayesClassifier or ngramNaiveBayesClassifier

## scikit-learn
## SVMClassifier.py
Run SVM algoritm to classify reviews into "positive" and "negative"
  - Call loadReviews
  - textProcessing is NOT called because the process is included in Vectorizer classes of scikit-learn
  - Call generateTrainingTestSet
  - Call linearSVMClassifier

#Results
- SVM gives a slightly better accuracy (~86%)
- In both cases, n-gram model gives better accuracy
- Removing stop words and stemming did not improve accuracy
