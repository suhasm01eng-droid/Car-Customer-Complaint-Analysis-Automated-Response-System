
# Customer Review Analysis and Generative AI Response System

## 1. Project Overview

This project analyzes customer reviews from connected-car mobile applications
using Python and Pandas.

The project identifies critical customer reviews using a rule-based approach
and analyzes common complaint keywords. Three detailed critical reviews are
then selected and processed using the Gemini Generative AI API to generate
personalized and empathetic customer-support responses.

---

## 2. Objectives

The main objectives of this project are:

- Load and understand a customer-review dataset.
- Clean and preprocess customer review text.
- Handle missing values.
- Analyze customer ratings.
- Identify critical reviews using a rule-based approach.
- Identify common complaint keywords.
- Select three detailed critical reviews.
- Use Generative AI to generate personalized customer responses.
- Save the final AI-generated responses for further use.

---

## 3. Dataset

### Dataset Name

OEM Connected-Car App Reviews Dataset:
Google Play User Feedback from 21 Automotive Companion Apps

### Source

Mendeley Data

### DOI

10.17632/fsrgtm6vf7.1

### Dataset Description

The dataset contains customer reviews of automotive connected-car
applications collected from Google Play.

The dataset contains review information such as:

- Institution/company
- Application name
- Review text
- Star rating
- Thumbs-up count
- Review date
- Application version
- Language

---

## 4. Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Collections / Counter
- Google Gemini API
- Google GenAI Python SDK
- Jupyter Notebook

---

## 5. Data Cleaning

A working copy of the original dataset was created so that the original
data remained unchanged.

The following cleaning steps were performed:

1. Empty review-title information was removed because the column contained
   no useful values.

2. Missing application-version values were replaced with "Unknown".

3. Review text was converted to lowercase.

4. Special characters and unnecessary non-alphanumeric characters were
   removed.

5. Extra spaces were removed from the review text.

6. A cleaned review column named `clean_review` was created.

7. Review length was calculated using the cleaned review text.

---

## 6. Exploratory Data Analysis

The following analysis was performed:

- Dataset dimensions
- Column names
- Dataset information
- Missing-value analysis
- Rating distribution
- Rating percentages
- Rating summary
- Review-length analysis
- Rating visualization

The dataset contains 24,103 customer reviews.

The rating distribution was:

- 1 Star: 10,494
- 2 Stars: 2,302
- 3 Stars: 1,960
- 4 Stars: 1,895
- 5 Stars: 7,452

---

## 7. Rule-Based Critical Review Identification

A simple rule-based approach was used instead of machine learning.

Reviews with a star rating less than or equal to 2 were classified as
critical reviews.

The rule used was:

    star_rating <= 2

This identified 12,796 critical reviews.

This approach makes the selection logic simple, transparent, and easy to
understand.

---

## 8. Complaint Keyword Analysis

The cleaned text from critical reviews was analyzed using Python string
processing and `collections.Counter`.

Common words and complaint-related terms were counted to understand the
issues frequently mentioned by customers.

The keyword analysis helps identify recurring problems in the customer
feedback without using a machine-learning model.

---

## 9. Selection of Critical Reviews

Three detailed 1-star reviews were selected for Generative AI processing.

The selected reviews were:

| Review Index | Company | Complaint Category |
|---|---|---|
| 21670 | Toyota | Login and Remote Vehicle Functions |
| 23398 | Lexus | Incorrect or Outdated Vehicle Data |
| 20425 | Toyota | Battery Drain and App Performance |

The reviews were selected based on:

- Very low star rating
- Detailed review content
- Clearly identifiable customer problems
- Different complaint categories

---

## 10. Generative AI Implementation

Google Gemini was used to generate personalized customer-support responses.

The Gemini API was connected using the Google GenAI Python SDK.

The prompt was designed to instruct the model to:

- Acknowledge the customer's specific problem.
- Apologize for the inconvenience.
- Show empathy.
- Address the actual complaint.
- Keep the response professional and concise.
- Avoid unsupported promises.
- Avoid claiming that the issue has already been resolved.
- Recommend contacting an appropriate support channel when further help
  is required.

The same prompt structure was reused for all three reviews while the
company, application, complaint category, and customer review were
inserted dynamically.

---

## 11. API Key Setup

The Gemini API key is required to run the Generative AI section.

The API key should NOT be stored directly in the notebook or uploaded to
GitHub.

The notebook uses an environment variable to provide the API key.

Example:

    import os
    from google import genai

    os.environ["GEMINI_API_KEY"] = input("Enter your Gemini API key: ")

    client = genai.Client(
        api_key=os.environ["GEMINI_API_KEY"]
    )

Never share your API key publicly.

---

## 12. Gemini Model

The project uses the Gemini model:

    gemini-3.8-flash

The Generative AI request is made using the Interactions API.

Example:

    response = client.interactions.create(
        model="gemini-3.8-flash",
        input=prompt
    )

    print(response.output_text)

---

## 13. Final Results

The final output contains:

- Company name
- Application name
- Star rating
- Complaint category
- Original customer review
- AI-generated customer-support response

The final results contain three selected customer reviews and their
corresponding AI-generated responses.

---

## 14. Output Files

The project generates the following output files:

- `final_customer_responses.csv`
- `final_customer_responses.xlsx`

These files contain the final selected reviews and the corresponding
Generative AI customer-support responses.

---

## 15. How to Run the Project

### Step 1

Install the required Python libraries.

### Step 2

Open the Jupyter Notebook.

### Step 3

Load the customer-review dataset.

### Step 4

Run the data cleaning and exploratory analysis sections.

### Step 5

Run the rule-based critical review filtering section.

### Step 6

Run the complaint keyword analysis.

### Step 7

Select the three detailed critical reviews.

### Step 8

Install and import the Google GenAI SDK.

### Step 9

Enter your Gemini API key when prompted.

### Step 10

Run the Generative AI sections to generate customer responses.

### Step 11

Run the final-results section.

### Step 12

The final CSV and Excel files will be generated.

---

## 16. Key Findings

The analysis identified a large number of low-rated customer reviews.

The selected detailed complaints showed issues involving:

- Login and authentication
- Remote vehicle functions
- Incorrect or outdated vehicle information
- Battery drain
- Application performance
- Navigation and usability

Generative AI was able to convert the selected complaints into
personalized and empathetic customer-support responses.

---

## 17. Conclusion

This project demonstrates a practical workflow for analyzing customer
feedback using Python and Generative AI.

Python and Pandas were used for data cleaning and analysis. A transparent
rule-based approach was used to identify critical reviews, while keyword
analysis helped identify common complaint themes.

Three detailed critical reviews were then processed using the Gemini API
to generate personalized customer-support responses.

The project demonstrates how traditional data analysis and Generative AI
can be combined to transform raw customer feedback into useful insights
and automated support responses.

---

## 18. Future Enhancements

Possible future improvements include:

- Sentiment analysis of all customer reviews.
- Automatic complaint-category classification.
- Dashboard creation using Power BI.
- Automated response generation for a larger number of reviews.
- Multilingual customer-support responses.
- Integration with a customer-support system.
- Monitoring customer complaints over time.
