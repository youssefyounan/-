# -
情感日记利用情感分析技术和自然语言处理,分析用户的日记内容,提供情绪洞察和写作建议,帮助用户更好地表达和理解自己的情感。
from textblob import TextBlob
from textblob.sentiments import NaiveBayesAnalyzer
import sys

# Function to analyze the sentiment of the diary entry
def analyze_sentiment(diary_entry):
    # Using TextBlob with the NaiveBayesAnalyzer for more detailed sentiment analysis
    blob = TextBlob(diary_entry, analyzer=NaiveBayesAnalyzer())
    
    # Getting the sentiment classification
    classification = blob.sentiment.classification
    positive = blob.sentiment.p_pos
    negative = blob.sentiment.p_neg
    
    # Generating feedback based on the sentiment analysis
    if classification == 'pos' and positive > 0.6:
        feedback = "Your diary entry reflects positive emotions. It's great to see you in a good mood!"
    elif classification == 'neg' and negative > 0.6:
        feedback = "Your diary entry seems to carry some negative emotions. It's okay to feel this way. Reflecting on these feelings is a step towards understanding them."
    else:
        feedback = "Your diary entry shows a mix of emotions. Exploring these diverse feelings can lead to deeper emotional insight."
    
    return feedback

# Function to simulate the diary entry process and sentiment analysis
def main():
    print("Welcome to 情感日记 - Your Emotion Diary Assistant\n")
    diary_entry = input("What's on your mind today? Write your diary entry here:\n")
    
    feedback = analyze_sentiment(diary_entry)
    print("\nFeedback on your entry:\n" + feedback)

if __name__ == "__main__":
    main()
