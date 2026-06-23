# Investigating AI-Driven Patterns in Amazon Reviews

This project analyzes a super large Amazon customer review dataset with approximately **65 million customer reviews** and about **52.4 GiB** of review and product metadata. The goal is to investigate whether duplicated, redundant, or highly similar review content can reveal suspicious review behavior potentially influenced by AI-generated or mass-produced text.

## Project Overview

The analysis uses big data processing and similarity-based text techniques to explore Amazon review patterns across review content, ratings, products, and categories. The source data was provided in Google Cloud Storage as nested Parquet files:

- Reviews: `gs://msca-bdp-data-open/final_project_reviews/reviews_parquet`
- Product metadata: `gs://msca-bdp-data-open/final_project_reviews/meta_parquet`

Because the raw dataset is extremely large, this repository includes the analysis notebook and presentation only. The original 65 million-review dataset is not uploaded to GitHub.

## Selected Presentation Visuals

### Review Title and Review Text Duplication

![Review title and review text duplication](assets/review-title-text-duplication.png)

### Common Words in 5-Star vs. 1-Star Reviews

![Common words in 5-star vs. 1-star reviews](assets/star-rating-common-words.png)

## Repository Contents

```text
.
├── assets/
│   ├── review-title-text-duplication.png
│   └── star-rating-common-words.png
├── notebooks/
│   └── amazon_reviews_analysis.ipynb
├── presentation/
│   └── amazon_reviews_final_project.pdf
├── .gitignore
├── README.md
└── requirements.txt
```

## Methods

The project uses:

- PySpark for distributed data loading, cleaning, transformation, and aggregation
- Exploratory data analysis for review volume, ratings, products, categories, and reviewer behavior
- Text cleaning and tokenization for review titles and review bodies
- MinHash-LSH similarity analysis to detect duplicated or near-duplicated review titles and review texts
- Matplotlib and Seaborn for visualizations

## Key Findings Highlighted

- The dataset scale is large enough to require distributed processing instead of local-only analysis.
- Review title duplication appears more common than full review text duplication.
- In the analyzed All Beauty sample, MinHash-LSH detected **476 pairs of duplicated or near-identical review titles**, while duplicate review texts were nearly nonexistent.
- Positive reviews emphasize words such as "great," "love," "good," and "easy."
- Negative reviews contain more functional complaint language, including words related to product failure, usability, compatibility, and unmet expectations.

## How to View

Open the notebook in Jupyter:

```bash
jupyter notebook notebooks/amazon_reviews_analysis.ipynb
```

Open the final presentation:

```bash
open presentation/amazon_reviews_final_project.pdf
```

## Notes

This repository is intended as a project portfolio artifact. It does not include the raw Amazon Reviews Archive because the data is too large for GitHub and should be accessed from the original cloud storage location used for the course project.
