This project analyzes sentiment in Amazon product reviews using various machine learning techniques.

**Data Description:**

* The dataset contains reviews for various Amazon products.
* Training data: 4000 reviews, 8 columns (name, brand, categories, primaryCategories, reviews.date, reviews.text, reviews.title, sentiment)
* Test data: 1000 reviews, 7 columns (same as training set except brand)

**Data Preprocessing:**

* Missing values in `reviews.title` were addressed by removing corresponding rows (13 total).
* Redundant columns (`brand` and `categories`) were dropped.
* `name` was transformed into product type categories (e.g., tablets, TVs).
* `reviews.title` and `reviews.date` were dropped as they weren't relevant for sentiment analysis.
* The data exhibited imbalanced sentiment, with positive reviews heavily outweighing negative and neutral ones.

**Text Preprocessing and Feature Engineering:**

* TF-IDF vectorization was applied to capture the importance of words within reviews.
* Reviews were tokenized and padded into sequences of equal length for model training.

**Model Training and Evaluation:**

* Several machine learning models were evaluated for sentiment classification: MultinomialNB, RandomForest, XGBoost, SVM, and Neural Networks with LSTM/GRU layers.
* SVM achieved the best overall performance:
    * High accuracy
    * Good F1 score
* While other models also showed good accuracy, their F1 scores were lower, particularly for Neural Networks with LSTM/GRU.

**Topic Modeling with NMF:**

* Non-Negative Matrix Factorization (NMF) identified ten latent topics within the reviews, offering insights into customer sentiment towards different aspects:
    * Product evaluation (Fire tablets)
    * Gifting (Fire tablets)
    * Smart home device sentiment
    * Kindle e-reader usability
    * E-reader comparisons
    * Overall tablet opinions
    * Tablet recommendations
    * Kindle e-book sentiment
    * Tablet durability and age-appropriateness
    * Parental controls

**Choice of NMF over LDA:**

* NMF assumes a mixture of topics within each review, leading to more generalizable topics compared to Latent Dirichlet Allocation (LDA), which assumes each review belongs to a single dominant topic.
