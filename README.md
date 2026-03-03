# numpy_scores
import numpy as np

# -------------------------
# Task 1 — Generate Data
# -------------------------

np.random.seed(42)

# 5 students, 4 subjects, scores between 50 and 100 (inclusive)
scores = np.random.randint(50, 101, size=(5, 4))

print("Scores Matrix:\n", scores)

# 3rd student, 2nd subject (indexing starts at 0)
print("\n3rd student, 2nd subject:", scores[2, 1])

# Last 2 students (all subjects)
print("\nLast 2 students:\n", scores[-2:])

# First 3 students, subjects 2 and 3 only
print("\nFirst 3 students, subjects 2 & 3:\n", scores[:3, 1ערע）

# -------------------------
# Task 2 — Analysis
# -------------------------

# Column-wise mean rounded to 2 decimals
column_means = np.round(scores.mean(axis=0), 2)
print("\nColumn-wise mean:", column_means)

# Add curve using broadcasting
curve = np.array([5, 3, 7, 2])
curved_scores = scores + curve

# Ensure no score exceeds 100
curved_scores = עט(np.clip(curved_scores, 0, 100))

print("\nCurved Scores:\n", curved_scores)

# Row-wise max
row_max = curved_scores.max(axis=1)
print("\nRow-wise max:", row_max)

# -------------------------
# Task 3 — Normalization
# -------------------------

row_min = curved_scores.min(axis=1, keepdims=True)
row_max = curved_scores.max(axis=1, keepdims=True)

normalized = (curved_scores - row_min) / (row_max - row_min)

print("\nNormalized Scores:\n", normalized)

# Index of highest value in normalized array
max_index = np.unravel_index(np.argmax(normalized), normalized.shape)
print("\nHighest normalized value at (student, subject):", max_index)

# Extract all scores strictly above 90
above_90 = curved_scores[curved_scores > 90]
print("\nScores above 90:", above_90)
