# LSApp User Segmentation Analysis

A comprehensive machine learning project that segments mobile app users based on their usage behavior using the LSApp dataset.

## Project Overview

This project analyzes the LSApp (Large dataset of Sequential mobile App usage) dataset to group 292 users according to how they interact with mobile applications. The dataset contains 599,635 app usage records collected through the uSearch Android application.

### Key Objectives

Segment users across multiple behavioral dimensions:

1. **Usage Variety**: Number of unique apps used  
2. **Usage Frequency**: Number of sessions  
3. **Session Duration**: Average time spent per session  
4. **Temporal Patterns**: Time of day when activity occurs  
5. **App Preferences**: Most frequently used app categories  
6. **Custom Clustering**: Additional behavioral insights  

---

## Dataset Information

- **Source**: [LSApp GitHub Repository](https://github.com/aliannejadi/lsapp)  
- **Records**: 599,635 app usage events  
- **Users**: 292 participants  
- **Collection Period**: Approximately 15 days per user  
- **Collection Method**: uSearch Android app  

### Data Structure

| Column | Description |
|--------|-------------|
| `user_id` | Unique user identifier |
| `session_id` | Unique session identifier |
| `timestamp` | Date and time of event |
| `app_name` | Name of the app |
| `event_type` | Event type (Opened, Closed, User Interaction, Broken) |

---

## Getting Started

### Prerequisites

```bash
Python 3.8+
pip install -r requirements.txt
```

### Installation

1. Clone the repository:

```bash
git clone <your-repository-url>
cd lsapp-user-segmentation
```

2. Install dependencies:

```bash
pip install -r requirements.txt
```

3. Download the LSApp dataset:
   - Download `lsapp_tsv.gz` from the LSApp repository  
   - Place it in the project root directory  
   - Extract the file before running the analysis  

---

## Running the Analysis

### Option 1: Jupyter Notebook (Recommended)

1. Start Jupyter:

```bash
jupyter notebook
```

2. Open `customer segmentation analysis.ipynb`  
3. Run all cells sequentially  
4. The notebook includes step-by-step explanations  

### Option 2: Python Scripts

Run the analysis directly:

```bash
python customer segmentation analysis.ipynb
```

---

## Project Structure

```
lsapp-user-segmentation/
├── README.md                              # Project documentation
├── requirements.txt                       # Python dependencies
├── customer segmentation analysis.ipynb   # Main analysis notebook
├── lsapp.tsv                              # Dataset (local only, not pushed to GitHub)
└── results/                               # Generated outputs
    ├── figures/                           # Visualizations
    ├── cluster_profiles/                  # Cluster analysis results
    └── models/                            # Saved models
```

---

## Methodology

### 1. Data Preprocessing

- Convert timestamps and extract time-based features  
- Categorize apps (Social Media, Games, Entertainment, etc.)  
- Calculate session durations  
- Handle missing or inconsistent values  

### 2. Feature Engineering

**User-Level Features (29 total)**:

- `num_unique_apps`: Number of distinct apps used  
- `num_sessions`: Total number of sessions  
- `avg_session_duration_min`: Average session length  
- `total_events`: Total usage events  
- `avg_events_per_session`: Event density  
- `avg_apps_per_session`: App switching behavior  
- `usage_std`: Daily usage consistency  
- `active_days`: Days with activity  
- `most_active_hour`: Peak usage hour  
- Time-of-day percentages (Morning, Afternoon, Evening, Night)  
- App category percentages  

### 3. Data Scaling

Three scaling methods were compared:

- **StandardScaler** (Z-score normalization) ✓ Selected  
- MinMaxScaler (0 to 1 normalization)  
- RobustScaler (median and IQR scaling)  

### 4. Dimensionality Reduction

**Principal Component Analysis (PCA)**:

- Reduces feature space while preserving most of the variance  
- Makes high-dimensional data easier to visualize  
- Highlights the most important behavioral features  

The first 10 components explain roughly 90% of the variance.

### 5. Clustering Algorithms

Four clustering techniques were evaluated:

| Algorithm | Type | Strengths |
|-----------|------|-----------|
| **K-Means** | Centroid-based | Fast, scalable, easy to interpret |
| **Hierarchical** | Hierarchical | Reveals cluster relationships |
| **DBSCAN** | Density-based | Handles noise and irregular shapes |
| **GMM** | Probabilistic | Soft clustering with probability scores |

### 6. Evaluation Metrics

- **Silhouette Score**: Measures cohesion and separation  
- **Davies-Bouldin Index**: Lower values indicate better clusters  
- **Calinski-Harabasz Index**: Higher values indicate better separation  

### 7. Optimal K Selection

The number of clusters is chosen using:

- Elbow method  
- Silhouette analysis  
- Davies-Bouldin minimization  
- Calinski-Harabasz maximization  

---

## Key Findings

Cluster characteristics may vary, but common patterns include:

### Heavy Users
- High app diversity  
- Frequent sessions  
- Longer session durations  
- Active throughout the day  

### Casual Users
- Moderate activity  
- Shorter sessions  
- Mostly evening or night usage  
- Focus on entertainment and social apps  

### Power Users
- Very active and consistent  
- Large variety of apps  
- Productivity and communication focused  

### Light Users
- Few apps  
- Infrequent sessions  
- Short interactions  
- Sporadic behavior  

---

## Visualizations

The project generates several visual outputs:

1. Event type distribution  
2. Top used apps  
3. App category breakdown  
4. Feature histograms  
5. Correlation matrix  
6. Scaling comparisons  
7. PCA explained variance plots  
8. Cluster evaluation graphs  
9. 2D and 3D cluster visualizations  
10. Radar charts and heatmaps  
11. Algorithm comparison charts  

---

## Technologies Used

- **Python 3.8+**
- **pandas, numpy**
- **matplotlib, seaborn**
- **scikit-learn**
- **scipy**
- **Jupyter Notebook**

---

## References

### Research Paper

```bibtex
@article{AliannejadiTOIS21,
    author = {Aliannejadi, Mohammad and Zamani, Hamed and Crestani, Fabio and Croft, W. Bruce},
    title = {Context-Aware Target Apps Selection and Recommendation for Enhancing Personal Mobile Assistants},
    journal = {ACM Transactions on Information Systems (TOIS)},
    year = {2021}
}
```

---

## Contributing

Contributions are welcome. Please feel free to submit a Pull Request.

1. Fork the repository  
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)  
3. Commit your changes (`git commit -m "Add new feature"`)  
4. Push to the branch (`git push origin feature/AmazingFeature`)  
5. Open a Pull Request  

---

## License

This project is open source and available under the MIT License.

---

## Authors

- Ndagha Kangoma – Initial work  

---

## Acknowledgments

- LSApp dataset creators  
- Università della Svizzera italiana (USI)  
- University of Massachusetts Amherst  

---

## Contact

For questions or feedback, please open an issue on GitHub or contact:

ndaghakangoma@gmail.com

---

## Future Work

Potential extensions include:

- Deep learning approaches (autoencoders, neural networks)  
- Temporal pattern analysis with time series methods  
- Predictive modeling for app usage  
- Real-time clustering  
- App recommendation systems  
- Cross-device usage analysis  
- Privacy-preserving clustering techniques  
