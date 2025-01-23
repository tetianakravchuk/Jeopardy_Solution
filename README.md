README for This is Jeopardy!

Overview

Welcome to the This is Jeopardy! project! This Python-based data analysis project explores a rich dataset of Jeopardy! questions, answers, and other attributes. You’ll apply your data manipulation skills to clean, filter, and analyze the dataset to uncover interesting insights and trends. Additionally, you’ll have the opportunity to build a self-quizzing tool to test your knowledge of trivia and potentially become the next Jeopardy! champion!

Project Goals

In this project, you will:
	•	Load and clean the Jeopardy! dataset.
	•	Investigate the dataset by creating functions to filter questions by keywords.
	•	Analyze the dataset to compute statistics, such as the average value of questions and the most common answers.
	•	Develop advanced analyses, such as tracking trends over time or studying category relationships.
	•	Build an interactive quizzing tool to test your trivia knowledge.

Dataset

The project uses a dataset named jeopardy.csv. The dataset contains the following columns:
	•	Show Number: The episode number of Jeopardy!
	•	Air Date: The date the episode aired.
	•	Round: The round of the game (e.g., Jeopardy, Double Jeopardy, Final Jeopardy).
	•	Category: The category of the question.
	•	Value: The monetary value of the question.
	•	Question: The question itself.
	•	Answer: The correct answer to the question.

Setup and Prerequisites

Prerequisites

To complete this project, you should be familiar with:
	•	Python programming.
	•	pandas library for data manipulation.
	•	Basic knowledge of regular expressions for cleaning text data.

Environment Setup

	1.	Install the required libraries:

pip install pandas


	2.	Place the jeopardy.csv file in the project directory.

Project Workflow

Step 1: Load and Inspect the Data

	•	Load the dataset using pandas.
	•	Investigate the column names and fix any formatting issues to make the data easier to manipulate.
	•	Use .head() to inspect the first few rows and identify cleaning needs.

Step 2: Clean the Data

	•	Rename columns to remove leading spaces.
	•	Use regular expressions to clean and convert columns like Value into numeric types for analysis.
	•	Handle missing values as appropriate.

Step 3: Filter Questions

	•	Write a function to filter questions based on keywords.
	•	Enhance the function to handle issues like capitalization and substring matches.

Step 4: Analyze the Data

	•	Calculate aggregate statistics, such as the average value of questions containing specific keywords.
	•	Count unique answers to understand patterns in responses.

Step 5: Advanced Exploration

	•	Investigate how question topics evolve over time.
	•	Study relationships between categories and rounds.
	•	Build a trivia quiz system to test your knowledge interactively.

Code Examples

Filter Questions by Keywords

def filter_data(data, words):
    filter = lambda x: all(word.lower() in x.lower() for word in words)
    return data.loc[data["Question"].apply(filter)]

Convert Value Column to Float

jeopardy_data["Float Value"] = jeopardy_data["Value"].apply(
    lambda x: float(x[1:].replace(',', '')) if x != "no value" else 0
)

Count Unique Answers

def get_answer_counts(data):
    return data["Answer"].value_counts()

Quiz Yourself

def quiz_user(data):
    random_question = data.sample(n=1).iloc[0]
    print(f"Question: {random_question['Question']}")
    user_answer = input("Your answer: ")
    if user_answer.lower() == random_question['Answer'].lower():
        print("Correct!")
    else:
        print(f"Wrong! The correct answer was: {random_question['Answer']}")

Future Ideas

	•	Explore how question complexity correlates with monetary value.
	•	Study the popularity of categories over time.
	•	Implement difficulty levels in the self-quizzing tool.
	•	Visualize trends using libraries like matplotlib or seaborn.

How to Run

	1.	Clone the repository and place jeopardy.csv in the project folder.
	2.	Execute the script to analyze the data:

python jeopardy_analysis.py


	3.	Test the self-quizzing feature:

quiz_user(jeopardy_data)