Student Performance Predictor
This was my ML project where i wanted to go beyond just training a model and actually make it interactive. The idea was to predict a student's final exam score based on their study habits and academic history — but with a twist. I added NLP sentiment analysis so the student's own words about how they feel about their studies also affect the prediction.
I found it interesting that confidence and mindset could actually influence academic outcomes, so i wanted to reflect that in the model somehow. TextBlob made that surprisingly easy to implement.

What it does
Takes a few inputs about a student — study hours per week, attendance rate, past exam scores — and predicts their final exam score using Linear Regression.
Then it asks the student: "How do you feel about your studies?"
TextBlob analyzes the response and adjusts the prediction:

Positive feedback → +5 marks
Neutral → no change
Negative feedback → -5 marks

Finally gives a Pass/Fail result based on the predicted score.

Example output
==================================================
        STUDENT PERFORMANCE PREDICTION
==================================================
  Student Name          : Kunal
  Study Hours/Week      : 7.0
  Attendance Rate       : 76.0%
  Past Exam Score       : 70.0
--------------------------------------------------
  Student Feedback      : I have studied well and fully confident
  NLP Sentiment         : Positive  (polarity: 0.50)
--------------------------------------------------
  Base Predicted Score  : 51.34 / 100
  Sentiment Adjustment  : +5 marks
  Final Predicted Score : 56.34 / 100
  Result                : PASS
==================================================

Dataset
708 student records across 10 features. Target variable is Final_Exam_Score.
Features used for prediction: Study Hours per Week, Attendance Rate, Past Exam Scores.
Other columns: Student ID, Gender, Parental Education Level, Internet Access, Extracurricular Activities, Pass/Fail label.
Mean final score is 58.77, score range 50-77, 50/50 pass fail split.

Tech Stack

Python, Jupyter Notebook
scikit-learn — Linear Regression model
TextBlob — NLP sentiment analysis
pandas, numpy — data handling
matplotlib — actual vs predicted bar chart visualization


How to run
bash# install dependencies
pip install -r requirements.txt

# for model training and visualization
jupyter notebook code.ipynb

# for interactive prediction
jupyter notebook predict_student.ipynb

Files
student-performance-predictor/
├── code.ipynb              # model training, evaluation, visualization
├── predict_student.ipynb   # interactive prediction with NLP
├── students_data.csv       # dataset - 708 students
├── requirements.txt        # dependencies
└── README.md

Model details
Algorithm: Linear Regression
Train/Test split: 80/20
Evaluation: R² Score and Mean Absolute Error
Sentiment adjustment: +5 for positive, 0 for neutral, -5 for negative (TextBlob polarity threshold 0.2)

What i learned
Combining ML with NLP in the same project was something i hadn't done before. The sentiment analysis part was honestly more interesting than the regression model itself. Also learned that simple models like Linear Regression can work really well when you pick the right features — attendance and past scores turned out to be the strongest predictors.

Things i'd add with more time

try Random Forest and compare accuracy with Linear Regression
build a simple web interface with Flask or Streamlit
use VADER or BERT instead of TextBlob for better sentiment accuracy
add more features like sleep hours and mental health score


Built as part of my final year projects. B.Tech CSE - AI/ML, GD Goenka University, Faridabad.