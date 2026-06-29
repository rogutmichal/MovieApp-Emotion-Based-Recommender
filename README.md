# MovieApp – Emotion-Based Movie Recommendation System

MovieApp is a C# application using **ML.NET** and SQLite to recommend movies based on emotion analysis of user reviews.  
The system combines user ratings, emotional movie profiles, and review text analysis to generate personalized recommendations.

---

## Features

- Fetching movie and review data from **The Movie Database API (TMDb)**.
- Emotion analysis of user reviews using a trained ML.NET model.
- Building emotional profiles for both movies and users.
- Generating movie recommendations based on emotional similarity.
- User rating management with filtering by genre and title.
- Displaying top recommended movies in the application interface.

---

## Emotion Model

The emotion classification model recognizes six emotion classes in reviews:

- sadness  
- anger  
- love  
- surprise  
- fear  
- joy  

The model (`emotion_model.zip`) was trained in the separate project  
[emocje](https://github.com/rogutmichal/emotion-prediction-model) and is loaded in this application using ML.NET `PredictionEngine` for text classification.

**Dataset used for training:**  
[Emotions Dataset for NLP (Kaggle)](https://www.kaggle.com/datasets/praveengovi/emotions-dataset-for-nlp)

---

## Database Structure

The SQLite database stores:

- **Movie** – movie details (title, description, genre, release date, popularity, poster path).  
- **Review** – movie reviews with predicted emotion scores (top 6 emotions).  
- **User** – user data (ID, name, role).  
- **Rating** – user ratings assigned to movies.

---

## Recommendation Process

1. Load all movies, reviews, and user ratings from the database.
2. Analyze reviews and assign emotional scores to each movie.
3. Build a user emotional profile based on rated movies and associated emotions.
4. Compute emotion weights for recommendation scoring.
5. Compare user and movie profiles using **cosine similarity**.
6. Return top-ranked movie recommendations.

---

## Technologies

- **C# / .NET MAUI** – application UI and business logic.
- **ML.NET** – emotion classification from text.
- **SQLite** – local storage for movies, users, reviews, and ratings.
- **TMDb API** – movie metadata and review data source.
- **Newtonsoft.Json** – JSON parsing.

---

## Screenshots

### Movie list
<img width="1912" height="932" src="https://github.com/user-attachments/assets/b01d0d79-0814-4b3a-9376-1723be76579e" />

### Recommendations
<img width="1882" height="776" src="https://github.com/user-attachments/assets/31434f28-24dc-4a3f-bc6b-f567cfe8771e" />

---

## Run Instructions

Configure your `appsettings.json` file with a TMDb API key:

```json
{
  "ApiKeys": {
    "MovieDb": "YOUR_API_KEY"
  }
}
