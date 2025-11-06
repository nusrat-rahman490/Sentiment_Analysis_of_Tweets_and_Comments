# 🧠 Sentiment Analysis of TikTok Comments (March–April 2025)

## 🎯 Project Goal
This project demonstrates **NLP (Natural Language Processing)** and **text analytics** skills by analyzing sentiments from 50 TikTok-related comments.  
Using Python and TextBlob, we classify each comment as **Positive**, **Negative**, or **Neutral**, and visualize the sentiment distribution.

---

## 🧩 Overview
- **Objective:** Analyze user-generated content to understand audience sentiment.  
- **Dataset:** 50 sample TikTok comments collected between **March and April 2025**.  
- **Goal:** Quickly extract insights that reflect audience perception of trending TikTok topics.  
- **Impact:** Shows ability to process real-world text data and visualize emotional tone — an important skill for product analytics and user experience research.

---

## 📁 Dataset
The dataset file is named:
`Sentiment_Analysis_50tweets_March_April2025.xlsx`

---
## 📍 File Location
`Desktop/Spreadsheet/Sentiment_Analysis_50tweets_March_April2025.xlsx`

---
### 🧾 Columns
| Column Name | Description |
|--------------|-------------|
| Tweet_ID     | Unique ID for each tweet/comment |
| Date         | Date between March–April 2025 |
| Username     | Username or commenter |
| Tweet_Text   | The text content of the tweet/comment |

---

## 🛠️ Tools & Technologies
- **Python 3**
- **Pandas** → For data manipulation  
- **TextBlob** → For sentiment polarity detection  
- **Matplotlib** → For data visualization  
- **Excel** → For storing and exporting sentiment results  

---

## 🚀 How to Run

1.**Clone the Repository**
```bash
git clone <repository-url>
cd Sentiment-Analysis-TikTok
```
2. **Ensure the Dataset Exists**  

Save your dataset in:  
`Desktop/Spreadsheet/Sentiment_Analysis_50tweets_March_April2025.xlsx`
```
3. **Run the Python Script**  
```bash
python Sentiment_Analysis_TikTok.py 
```
---

## 🧮 Sentiment Formula

Each comment’s sentiment is determined using **TextBlob polarity**:

- **Polarity Range:** -1.0 (Negative) → +1.0 (Positive)  
- If polarity > 0.1 → **Positive**  
- If polarity < -0.1 → **Negative**  
- Otherwise → **Neutral**

---

### 🧠 Python Code

```python
import pandas as pd
from textblob import TextBlob
import matplotlib.pyplot as plt
import os

# ---------- Step 1: Load the dataset ----------
file_path = "/home/nusrat/Desktop/Spreadsheet/Sentiment_Analysis_50tweets_March_April2025.xlsx"
df = pd.read_excel(file_path)

print("✅ Dataset Loaded Successfully!")
print(df.head())

# ===============================
# 2. Sentiment Analysis
# ===============================
def analyze_sentiment(text):
    blob = TextBlob(str(text))
    polarity = blob.sentiment.polarity
    if polarity > 0.1:
        return "Positive"
    elif polarity < -0.1:
        return "Negative"
    else:
        return "Neutral"

df["Sentiment"] = df["Tweet_Text"].apply(analyze_sentiment)

# ===============================
# 3. Summary Statistics
# ===============================
sentiment_counts = df["Sentiment"].value_counts()
print("\n📊 Sentiment Distribution:")
print(sentiment_counts)

# ===============================
# 4. Visualization
# ===============================
plt.figure(figsize=(6, 6))
plt.pie(
    sentiment_counts,
    labels=sentiment_counts.index,
    autopct="%1.1f%%",
    startangle=140,
    shadow=True,
)
plt.title("Sentiment Distribution of 50 TikTok Comments (Mar–Apr 2025)")
plt.show()

# ===============================
# 5. Save Results
# ===============================
output_path = os.path.expanduser("~/Desktop/Spreadsheet/Sentiment_Results_March_April2025.xlsx")
df.to_excel(output_path, index=False)
print(f"\n✅ Sentiment results saved to: {output_path}")
```
---

## 📊 Sample Insights

- **Positive Sentiment:** Majority of users express enjoyment and excitement about TikTok content.  
- **Negative Sentiment:** Small portion of users show frustration or disinterest.  
- **Neutral Sentiment:** Common among informational or casual posts.  

**Recommendation:**  
- Promote content categories with higher positive sentiment.  
- Monitor negative feedback trends for potential user experience improvements.
---
## 🏁 Output

After running the script:

- A new file `Sentiment_Results_March_April2025.xlsx` will be created containing the original data plus sentiment labels.  
- A pie chart will display the sentiment distribution visually.
---

### 🧩 Example Output Preview

| Tweet_Text                        | Sentiment |
|----------------------------------|-----------|
| “I love TikTok’s new features!”   | Positive  |
| “Not impressed with the update.”  | Negative  |
| “This video is fine.”             | Neutral   |


---
## 🧭 Project Impact

- ✅ Demonstrates understanding of user sentiment.  
- ✅ Combines data analysis, NLP, and visualization.  
- ✅ Reflects ability to turn unstructured text into actionable insights.
---

## 📅 Date Range

Data covers: March 1, 2025 → April 30, 2025

---

