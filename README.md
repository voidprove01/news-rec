## **Overview**

This project presents a hybrid **two-stage news recommendation system** designed to provide personalized, relevant, and engaging news article recommendations to users. The system is implemented entirely in Jupyter notebooks for clarity and ease of exploration.

The **two-stage architecture** is structured as follows:

1. **Recall Stage:**
   - This stage identifies a **broad set of candidate articles** for each user from a large article pool.
   - Implements a **hybrid recall mechanism**, combining:
     - **Collaborative filtering:** Suggests articles based on similarities between users or items.
     - **Embedding-based similarity:** Leverages pre-trained embeddings to recommend semantically similar articles.
     - **YouTube DNN method:** Uses user-item embeddings and deep learning to generate diverse and personalized candidates.
   - **Approximate Nearest Neighbor (ANN):** Utilized to efficiently retrieve similar articles, ensuring scalability for datasets with millions of users and items.
   - Prioritizes efficiency to ensure fast candidate generation even for large-scale datasets.

2. **Ranking Stage:**
   - Refines the candidate articles from the recall stage into a **ranked list** based on personalized relevance scores.
   - Utilizes advanced feature engineering to compute:
     - **Temporal weights:** Accounts for the time difference between user interactions and article creation.
     - **Positional weights:** Captures the impact of interaction history recency.
     - **Content-based features:** Explores semantic similarities between articles.
   - Employs a **LightGBM-based ranking model**, which balances interpretability, speed, and accuracy.

This system is built to address challenges commonly encountered in recommendation systems, such as:
- **Cold Start:** A fallback mechanism recommends popular articles to users with sparse interaction histories.
- **Scalability:** Efficient data preprocessing and lightweight recall ensure the system can handle large-scale datasets.
- **Evaluation:** Uses Mean Average Precision (MAP) to assess performance.

The project is modular and extensible, making it a great starting point for building production-grade recommendation systems.

### **Execution Steps**

1. **Clone the Repository**
   - Clone the repository to your local machine:
     ```bash
     git clone https://github.com/yourusername/news-recommendation-system.git
     cd news-recommendation-system
     ```

2. **Install Dependencies**
   - Install the required Python packages:
     ```bash
     pip install -r requirements.txt
     ```

3. **Download the Dataset**
   - Obtain the dataset required for the project:
     - Download from the links contained in "DataA1121.md"
   - Save the dataset in the `data/` directory:
     ```bash
     mkdir -p data
     mv path_to_downloaded_data data/
     ```

4. **Launch Jupyter Notebook**
   - Open Jupyter Notebook or JupyterLab:
     ```bash
     jupyter notebook
     ```

5. **Run the Notebooks**
   - Execute the notebooks in the following order:
     1. `Baseline.ipynb`:
        -implements a baseline recommendation system using item-to-item collaborative filtering.
     2. `EDA.ipynb`:
        - Run the `0_eda.ipynb` notebook to:
          - Understand the distribution of user interactions, article metadata, and timestamps.
          - Identify missing or anomalous data points.
          - Visualize key trends in user behavior and article popularity.
     3. `Hybrid Recall.ipynb`:
        - Implements the hybrid recall mechanism, including:
          - Collaborative filtering.
          - Embedding-based similarity.
          - YouTube DNN.
          - Approximate Nearest Neighbor (ANN) methods.
     4. `Feature_engineering.ipynb`:
        - Prepares the dataset by:
          - Generating user interaction histories.
          - Performing negative sampling.
          - Handling cold-start scenarios.
        - Extracts user and article features using:
          - User's last click and historical behavior.
          - Recall list and article metadata.
          - Embedding vectors.
        - Generates labels to form the final supervised learning dataset.
   
     5. `Ranking.ipynb`:
        - Ranks the recalled articles using features like:
          - Temporal weights.
          - Positional weights.
          - Content-based similarity.
        - Trains LightGBM-based ranking models for personalized recommendations.
     ```
7. **Inspect Results**
   - Analyze results and visualizations in the notebooks:
     - Candidate articles generated in the recall stage.
     - Ranked lists of articles for each user.

### Acknowledgement
   This project is inspired by [fun_rec](https://github.com/datawhalechina/fun-rec).
