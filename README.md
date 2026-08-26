# Choices13k: Predicting Choice Behavior in Risky Gambles

Analyzes the [Choices13k](https://github.com/jcpeterson/choices13k) dataset of human choices between pairs of lotteries (gambles) with and without feedback, aiming to predict the choice rate for option B (`bRate`) from problem and gamble features.

## Contents

- `analysis.ipynb` — full analysis pipeline:
  1. **Data fetching** — downloads `c13k_problems.json` (problem/gamble definitions) and `c13k_selections.csv` (choice outcomes) from the Choices13k repository, and validates the JSON.
  2. **Data preparation** — merges selections and problems on problem ID into a single dataframe; investigates duplicate problem IDs (the dataset has 13,006 unique risky-choice problems but 3,124 extra rows, because some problems were run both with and without outcome feedback).
  3. **Exploratory analysis** — inspects missing values, the distribution of the target `bRate` (roughly bell-shaped, centered ~0.5–0.6), and a feature correlation heatmap (most features are largely uncorrelated with each other).
  4. **Modeling** — builds predictive models of `bRate` from gamble/problem features.

## Key columns

| Column | Description |
|---|---|
| `problem` | Unique internal problem ID |
| `n` | Number of subjects run on the problem |
| `feedback` | Whether subjects saw the outcome of forgone options |
| `bRate` | Target: frequency with which subjects chose Gamble B |
| `ha`, ... | Gamble structure fields (outcome/probability pairs for each option) |

## Usage

Open `analysis.ipynb` in Jupyter; it downloads the required data files automatically if not already present locally.
