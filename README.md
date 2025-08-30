#  Classifying Social Media Texts into Multiple Hate-Based Categories for Indian languages 
Team_6_NLP Blog Link: https://dev.to/batul02/classifying-social-media-texts-into-multiple-hate-based-categories-for-indian-languages-1me9


## Problem Statement 
Developing an effective system for hate speech detection and categorization in Hindi by leveraging Hindi WordNet for initial positive and negative word scores, and subsequently expanding the lexicon using Sysnet. This approach addresses the challenge of limited sentiment analysis tools tailored for Hindi, ensuring a more comprehensive understanding of linguistic nuances and cultural contexts.

### Proposed Pipline 
- Subjectivity Analysis: The process of subjectivity analysis involves identifying subjective tweets and filtering out objective content, laying the foundation for hate speech detection.
- Building a Hate Speech Lexicon: The algorithm involves constructing a lexicon of negative words and hate verbs to accurately identify hate speech, enhancing the precision of detection.
- Identifying Theme-Based Nouns: The inclusion of theme-based nouns ensures that hate speech is contextually relevant, capturing politically significant words and other relevant nouns.

### Subjective Analysis
- Subjectivity analysis simplifies the corpus by focusing on subjective tweets, which are more likely to contain hate speech, rather than objective ones.
- We utilize Hindi WordNet to assign positivity and negativity scores to words in the dataset.
- Using the SUBJCLUE lexicon, we match each key to its appearance in the dataset and assign corresponding positive and negative scores.
- The total score for each tweet or sentence is determined based on these assigned scores.
- Objective tweets are identified and marked as "not hate" by filtering out those with low subjectivity scores.
- We used a variety of values as the limiting values that make a tweet worth investigating further, and decided that all tweets with a score above 1.0 or below -0.5 were subjective enough to be heavy contributors towards hate speech.
- The lower limit is numerically lesser than the upper one because we found that the sentences marked negatively by the word sentiment analysis were more likely to contain hate speech.

![image](https://github.com/chaitanyabalajireddy/Team_6_NLP/assets/91625648/6e3f9247-34fb-4800-88eb-097deac67f42)

### Growing our Lexicon
- Extracting synonym sets (SYNSET) from 'Synset.txt' to expand the lexicon.
- Utilizing the Stanza library for Hindi NLP, including tokenization and part-of-speech tagging.
- Identifying verbs from the processed dataset for analysis.
- Categorizing strongly and weakly negative words from the SUBJCLUE lexicon.
- Developing a function (Getsynset) to retrieve synonym sets and enrich the lexicon.
- Adding verbs from predefined lists and SYNSET to expand the lexicon.
- Compiling the expanded lexicon for hate speech classification.

### Benefits of Using SYNSET
-	Comprehensive Coverage: SYNSET ensures that the lexicon covers a broad spectrum of words with similar meanings, making the detection process more robust.
- Contextual Understanding: By including synonyms, the model gains a better understanding of the context in which certain words are used, improving the accuracy of hate speech detection.
- Adaptive Lexicon: The lexicon becomes adaptive and dynamic, capable of evolving as new synonyms and expressions of hate speech emerge over time.

### Theme-Based Nouns
To accurately detect hate speech, it is essential to identify and analyze not only verbs and adjectives but also the nouns that often appear in hateful contexts. This step involves a detailed examination of noun phrases (NPs) within the corpus to pinpoint those frequently used in hateful tweets. By doing so, we can create a targeted list of nouns that enhance the precision of our hate speech detection model.

## Final Testing

The lexicons are tested on the corpus to evaluate their impact on hate speech detection accuracy. The algorithm’s components are tested individually to assess each lexicon’s contribution. The following criteria are used to classify tweets:

- Strongly Hateful: Tweets with two or more strongly negative words, or a combination of strongly negative words with hate-verbs or theme-based nouns.
- Weakly Hateful: Tweets with one strongly negative word or a combination of weakly negative words with theme-based nouns or hate-verbs.
- Non-Hateful: Tweets that do not meet the above criteria.

The results are compared with the manually defined objective results using precision, recall, and F-score metrics.

![image](https://github.com/chaitanyabalajireddy/Team_6_NLP/assets/91625648/d8b28af3-b7d9-409c-bef9-9b2283ea18a9)

As you can see, the hate-verbs alone do not make too much of a difference to the accuracy of our model, but adding the themed-noun lexicon improves it relatively significantly.

![image](https://github.com/chaitanyabalajireddy/Team_6_NLP/assets/91625648/e0429dcd-bc18-4ae3-9cbe-4f98f94d1f08)

Clearly, using subjectivity clues makes a very significant improvement to the accuracy of our hate-speech detector (nearly 7% increase in the F-score), which shows the importance of checking for contextual nouns while searching for and detecting hate speech. Another noteworthy factor is how the Recall is much higher than the precision; much higher, in fact, than the Recall value of the original project we referred to even though the precision we get is relatively lower. We argue this is due to our algorithm being efficient with ensuring that the hate-speeches are tagged correctly, as are the innocuous tweets. Thus, it leaves few false negatives (i.e. misses) behind. There are, however, relatively more false positives which takes away from precision. We argue that this is caused by our objective criterion (as described above) not being particularly objective at separating weak hate from strong hate because of the misalignment between criteria used by the corpus to tag hate speeches, and the criteria we ourselves use to segregate them. However,our algorithm compares favourably to the original in terms of segregating non-hate tweets from hateful tweets (about 66% precision in segregating non-hate) because of the criteria being more objective.

![image](https://github.com/chaitanyabalajireddy/Team_6_NLP/assets/91625648/cc296eff-600a-429b-ba7d-d202cb70a59c)

## Conclusion
The detection of hate speech in widely spoken languages like Hindi is increasingly important in today's digital era. Our model employs a rule-based approach to identify lexical patterns, allowing us to detect and quantify hate speech with reasonable precision. A key component of our algorithm is the analysis of subjectivity, which significantly enhances the accuracy of hate speech detection. Additionally, we categorize the detected hate speech to provide a more detailed understanding of the content, which helps prioritize our actions if needed.









