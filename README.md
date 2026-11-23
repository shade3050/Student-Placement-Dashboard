# Student Placement Dashboard

A web-based dashboard for a college placement cell to track student placement readiness, manage student records, and monitor company recruitment drives.

## Project Description

The dashboard gives a placement cell three views:

- **Overview** — headline stats (registered students, active drives, students placed, average readiness score), a placement-rate-by-branch breakdown, and a list of the students with the highest readiness scores.
- **Students** — a searchable directory of all students with branch, CGPA, backlog count, current status, placed company (if any), and a readiness score. New students can be added through a form. Clicking a row opens a detail panel with full profile and skill tags.
- **Placement Drives** — cards for each company drive showing role, package, date, applicant/shortlist/hire counts, and current stage. New drives can be added through a form.

Each student is given a **readiness score** (0–100) shown as a circular gauge. The score is currently computed with a transparent heuristic formula based on CGPA, backlog count, internship count, and number of skills listed. This is designed as a stand-in for a proper machine learning model — the `dataset/` folder included here is structured so a classification/regression model (e.g. logistic regression or a decision tree predicting placement likelihood) can be trained on it directly.

## Tech Stack

- HTML, CSS, and vanilla JavaScript — no framework or build step
- All data is currently in-memory (hardcoded sample records + anything added during a session); it resets on page refresh since there is no backend attached yet

## Folder Structure

```
├── source_code/
│   └── index.html          # the full application (single file)
├── dataset/
│   ├── students_dataset.csv  # 160 synthetic student records
│   └── drives_dataset.csv    # 6 synthetic placement drive records
├── README.md
└── Project_Report.docx
```

## How to Run

**Locally:**
1. Download `source_code/index.html`
2. Open it directly in any modern browser — no server or install required

**Deploying (e.g. Netlify):**
1. Drag and drop the `source_code` folder (or just `index.html`) onto Netlify's deploy area, or connect the GitHub repo and set the publish directory to `source_code`
2. No build command is needed

## Dataset

`students_dataset.csv` contains 160 synthetic student records with: student ID, name, branch, CGPA, backlog count, internship count, skills, application status, placed company, and a computed readiness score.

`drives_dataset.csv` contains 6 synthetic company drive records with: company, role, package, date, applicant/shortlist/hire counts, and stage.

Both are synthetic data generated for this project and do not represent real students or companies.

## Current Limitations / Future Scope

- No backend — data does not persist between sessions
- Readiness score is a heuristic, not a trained model
- Planned next steps: a small backend (e.g. Node/Express + MongoDB) for persistence, and a trained ML model on the provided dataset to replace the heuristic readiness score
