# Senior Well-being: Twitter Analysis

## Overview
NLP analysis of 57,139 Canadian tweets about senior citizens to understand
public concerns and sentiment during the COVID-19 pandemic. This social
welfare project provides insights for policymakers to improve quality of
life for vulnerable elderly populations.

## Research Questions
- What are Canadians most concerned about regarding senior well-being?
- What is the overall sentiment toward senior citizens on social media?
- How do concerns vary across Canadian provinces?
- Which topics dominate the conversation around senior well-being?

## Dataset
- 57,139 tweets collected via Twitter API
- Keywords: senior citizens, elderly, elder, old age + COVID-19 related terms
- Geographic coverage: All major Canadian provinces
- Time period: 2018-2022

## Pipeline

### 1. Data Collection
- Twitter API with senior citizen and COVID-19 keywords
- Geographic filtering for Canadian provinces

### 2. Text Preprocessing
- URL, mention, emoji removal using tweet-preprocessor
- Lowercase conversion and punctuation removal
- Stopword removal using NLTK
- Lemmatization using WordNetLemmatizer

### 3. BERT Embeddings
- Generated 768-dimensional embeddings for all 57,139 tweets
- Used BERT (bert_en_uncased_L-12_H-768_A-12) from TensorFlow Hub
- Batch processing (1,000 tweets per batch) for memory efficiency
- Cosine similarity filtering against "senior citizen" reference embedding
- Removed tweets with cosine score < 0.7 as irrelevant

### 4. Sentiment Analysis
- RoBERTa (cardiffnlp/twitter-roberta-base-sentiment) from HuggingFace
- Specifically trained on Twitter data — more accurate than generic models
- Three classes: Negative (1), Neutral (2), Positive (3)

### 5. Topic Modeling (BERTopic)
- Discovered 9 distinct topics from 57,130 relevant tweets
- Topics identified:

| Topic | Theme | Size |
|---|---|---|
| 0 | Community Care & Volunteering | 3,617 |
| 1 | Financial & Housing Concerns | 3,103 |
| 2 | Senior Sports & Activities | 2,538 |
| 3 | Indigenous Elders | 2,432 |
| 4 | Transportation & Mobility | 2,053 |
| 5 | Vaccination & Health | 1,791 |
| 6 | COVID-19 Impact | 1,697 |
| 7 | Elderly Men & Women | 1,561 |
| 8 | Respect for Elders | 1,374 |

### 6. Visualization
- Cosine score distribution by province (box plots)
- Sentiment distribution (pie chart)
- Sentiment by province (stacked bar chart)
- Word clouds per topic

## Key Findings
- Ontario dominates Twitter conversation about seniors (27,148 tweets)
- Majority of tweets are neutral in sentiment
- COVID-19 and vaccination are significant concerns
- Financial hardship and housing frequently discussed
- Indigenous elder well-being represents a distinct conversation thread
- Transportation and mobility are recurring challenges

## Technologies
- Python, Pandas, NumPy
- TensorFlow, HuggingFace Transformers
- BERT (TensorFlow Hub)
- RoBERTa (cardiffnlp/twitter-roberta-base-sentiment)
- BERTopic
- NLTK, tweet-preprocessor
- Plotly, Matplotlib, WordCloud

## Social Impact
This analysis provides actionable insights for:
- Policymakers addressing senior financial concerns
- Healthcare providers understanding vaccination hesitancy
- Transportation planners improving senior mobility
- Indigenous community organizations supporting elder well-being
