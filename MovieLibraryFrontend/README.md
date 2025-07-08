# Movie Library Frontend

This is the **frontend** for the Movie Library application, built with React. It allows users to browse, search, and explore movies and TV shows using data from [The Movie Database (TMDb) API](https://www.themoviedb.org/documentation/api). Users can view detailed information, images, trailers, and similar titles for each movie or TV show. Review features require a separate backend API (not included here).

---

## 📺 Project Demo Videos

- **Full Project Overview:**  
  [Watch Movie Library.mp4](./media/Movie%20Library.mp4)

- **Add Review Demo (Movie/TV Series):**  
  [Watch Movie Library - Review.mp4](./media/Movie%20Library%20-%20Review.mp4)

---

## Folder Structure

```
MovieLibraryFrontend/
├── public/
├── src/
│   ├── components/
│   ├── pages/
│   ├── services/
│   ├── App.js
│   └── ...
├── .env.production
├── package.json
└── README.md
```

## Environment Variables

Environment variables are set in `.env.production` (or `.env` for development):

```env
VITE_APP_MOVIE_API_BASE_URL=https://api.themoviedb.org
VITE_APP_MOVIE_API_LANGUAGE=en-US
VITE_APP_MOVIE_TOKEN=<your_tmdb_token>
VITE_APP_IMAGE_URL=https://image.tmdb.org/t/p
VITE_APP_REVIEW_API_BASE_URL=<your_dotnet_project_url>
```

- `VITE_APP_MOVIE_API_BASE_URL`: TMDb API base URL.
- `VITE_APP_MOVIE_API_LANGUAGE`: Language for TMDb API.
- `VITE_APP_MOVIE_TOKEN`: Token for TMDb API.
- `VITE_APP_IMAGE_URL`: Base URL for images.
- `VITE_APP_REVIEW_API_BASE_URL`: Your backend API for reviews.

## Running the Frontend

1. Open a terminal in the `MovieLibraryFrontend` folder.
2. Install dependencies:
   ```sh
   npm install
   ```
3. Set up your `.env.production` or `.env` file as shown above.
4. Start the frontend:
   ```sh
   npm run dev
   ```
   The app will be available at [http://localhost:5173](http://localhost:5173) by default.

### Using Review Features

- If you want to use review features, you must also run the backend API and set `VITE_APP_REVIEW_API_BASE_URL` accordingly.
- If the backend is not running or not configured, review features will be disabled or show errors.

---

**Note:** Replace `<your_tmdb_token>` with your actual TMDb API token.

## Features

- **Browse Movies & TV Shows:**  
  View a paginated list of popular movies and TV shows fetched from TMDb.

- **Search:**  
  Search for movies or TV shows by title.

- **Genres:**  
  - View genres for movies and TV shows, fetched from the TMDb API.
  - Click on any genre to see a list of movies or TV shows belonging to that genre (using the TMDb `/discover` endpoint).
  - **Note:** You cannot search for movies or TV shows by both genre and keyword at the same time, because the TMDb API does not support searching by genre in the `/search` endpoint. Genre-based filtering is only available via the `/discover` endpoint, which does not support keyword search.

- **Sort Options:**  
  - Sort movies and TV shows by "Popular" or "Top Rated" using the TMDb `/movie/popular`, `/movie/top_rated`, `/tv/popular`, and `/tv/top_rated` endpoints.
  - **Note:** Sorting by "Popular" or "Top Rated" cannot be combined with search or genre filtering, because the `/search` endpoint does not support sorting, and the `/discover` endpoint does not provide direct access to these sort types.

- **Movie/TV Show Details:**  
  View detailed information including title, release date, rating, genres, description, and poster/backdrop images.

- **Image Gallery:**  
  Browse a gallery of images/posters for each movie or TV show.

- **Similar Titles:**  
  Discover similar movies or TV shows based on the current selection.

- **Watch Trailers:**  
  Watch official trailers directly via YouTube links.

- **User Reviews:**  
  - View user-submitted reviews for each movie or TV show.
  - Add your own review (name and comment) for any title.
  - Reviews are stored and retrieved from a custom .NET backend API.

- **Share Functionality:**  
  Share movie or TV show details via social media or by copying a direct link.

## API Limitations & UI Behavior

- **Genre Filtering:**  
  - Filtering by genre uses the `/discover/movie` and `/discover/tv` endpoints.
  - You cannot combine genre filtering with keyword search.

- **Sorting:**  
  - Sorting is only available via the "Popular" or "Top Rated" endpoints.
  - Cannot be combined with search or genre filtering.

- **UI Behavior:**  
  - Only one of search, genre, or sort can be active at a time, matching TMDb API capabilities.

- **Pagination:**  
  - TMDb API supports pagination for pages 1 to 500 only.
  - If you request a page number greater than 500, an error message is shown.

---

**Note:** This project uses the TMDb API but is not endorsed or certified by TMDb.