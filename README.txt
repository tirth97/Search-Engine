Project requirements: 
python 2.J
Java 8
BeautifulSoup - https://github.com/akalongman/python-beautifulsoup/blob/master/LICENSE
nltk - https://github.com/nltk/nltk/blob/develop/LICENSE.txt

Other requirements are present in requirements.txt which can be installed by using pip install requirements.txt

All required intermediate files for all tasks are included in the zip provided.

Third Party Dependencies:
Java requires lucene(4.7.2)  https://archive.apache.org/dist/lucene/java/4.7.2/
Following jar files from the lucene library need to be added in our project:
1) lucene-core-4.7.2.jar
2) lucene-queryparser-4.7.2.jar
3) lucene-analyzers-common-4.7.2.jar.
To make any chances, please refer to official documentation http://lucene.apache.org/core/documentation.html

Preprocessing:
Unzip contents of downloaded zip file.
Run parser.py which will generate query.txt and parsed_corpus directory.

Format for Document Scores: 
For each query, a file will be generated in the format system_queryID.txt
eg. tfidf_1.txt
Every record is in the format: Query_ID Q0 DOC_ID Rank Score System
Top 100 scores are present in document_scores


Phase 1

Task 1:
1) TF-IDF Baseline: 
- Navigate to python/Tfidf Baseline folder
- Run python task1.py

2) Query Likelihood Model (Dirichlet Smooth)
- Navigate to python/Dirichlet Baseline folder
- Run python task1.py

3) BM25 Baseline:
- Navigate to python/BM25 Baseline folder
- Run python task1.py

4) Lucene Baseline:
- Navigate to java folder
- Run file src/task1.java

Task 2:
5) Pseudo-Relevance Feedback on BM25 Baseline
- Navigate to python/BM25 Pseudo Relevance folder
- Run python pseudo_relevance_query_expansion.py to generate modified_query.txt
- Run bm25.py

6) Semantic Query Expansion using Thesauri on BM25
- Navigate to python/BM25 Query Expansion Thesaurus folder
- Run task2.py to generate modifiedQuery.txt
- Run task1.py to compute BM25 scores.

Task 3:
7) Stopping on BM25 Baseline
- Navigate to python/BM25 Stopping folder
- Run python task1.py 
- Ensure common_words is present in the directory

8) Stopping on TF-IDF Baseline
- Navigate to python/Tfidf Stopping folder
- Run python task1.py 
- Ensure common_words is present in the directory

Cleaning Stemmed data: 
- Go to python/CleaningStemData
- Run clean_stem_data.py to generate StemmedData from cacm_stem.txt
9) Stemming on BM25 Baseline
- Navigate to python/BM25 Stemming folder
- StemmedData folder is used as corpus and cacm_stem.query.txt is used as query file.
- Run python task1.py 
- Ensure common_words is present in the directory

10) Stemming on TF-TDF Baseline
- Navigate to python/Tfidf Stemming folder
- StemmedData folder is used as corpus and cacm_stem.query.txt is used as query file.
- Run python task1.py
- Ensure common_words is present in the directory

Stemming analysis for task 3 - b is done in stem_analysis.txt

Phase 2:
- Navigate to python/Snippet Generation
- Run snippet.py
- Snippets are generated in snippets directory as html files.
- Open HTML files in browser to view highlighting.
- First line mentions all query terms. After that each document name is followed by its snippet(highlighted by a bold font)
- The documents and their snippets are ordered according to BM25 baseline ranks

Phase 3:

11) Query Expansion with Pseudo Relevance and Stopping on BM25 Baseline
- Navigate to python/BM25 Pseudo Relevance Stopping folder
- Run python pseudo_relevance_query_expansion.py to generate modified_query.txt
- Run bm25.py

Evaluation:
For the runs 1 to 8 and 11, Evaluation is performed in the following format:
cacm.rel.txt is used for relevance judgement.
Run evaluation.py in their respective directories to generate the following results:
1.MAP and MRR.txt generates MAP and MRR for the retrieval model.
2.Precision and recall details are generated for every query_id in precision_recall directory in the format Query_ID Q0 DOC_ID Rank Score Relevance(R/N) Precision Recall
3.Precision at K = 5 and 20 is generated in precision_at_5_score,txt and precision_at_20_score.txt 
Queries that dont have entries in relevance judgement file are not considered for evaluation.

Extra Credit Spelling Correction:
- navigate to python/Extra Credit Spelling Correction
- run extraCredit.py and enter query in command line interface.  

** parser.py might have compatibility issues with Windows ands Linux since it was designed for MacOS.
