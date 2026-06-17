# Credit Risk Prediction App

A Streamlit web app that predicts whether a loan applicant represents a **good** or **bad** credit risk, based on the [German Credit Risk dataset](https://www.kaggle.com/datasets/uciml/german-credit). The app uses a trained ExtraTrees classifier and label encoders to turn user input into a prediction in real time.

<table>
  <tr>
    <td><img src="https://github.com/user-attachments/assets/f401a8ce-ca21-4742-88b4-6e46931e5bb7" /></td>
    <td><img src="https://github.com/user-attachments/assets/dc070d32-cf47-4458-b467-6a7c7251ffdf" /></td>
  </tr>
</table>


## Demo

Enter applicant details (age, sex, job category, housing, savings, checking account, credit amount, loan duration) into the form, click **Predict Risk**, and the app returns a **GOOD** or **BAD** credit risk classification.

## Project Structure

```
.
├── app.py                          # Streamlit app
├── train_model.ipynb                # Notebook used to train the model and encoders
├── extra_trees_credit_model.pkl    # Trained ExtraTrees classifier
├── Sex_encoder.pkl                 # Label encoder for "Sex"
├── Housing_encoder.pkl              # Label encoder for "Housing"
├── Saving accounts_encoder.pkl      # Label encoder for "Saving accounts"
├── Checking account_encoder.pkl     # Label encoder for "Checking account"
├── requirements.txt
└── README.md
```

## Dataset

This project uses the **German Credit Risk** dataset, originally from the UCI Machine Learning Repository and commonly hosted on Kaggle. It contains 1,000 entries of loan applicants with attributes such as age, sex, job, housing situation, savings and checking account status, credit amount, and loan duration, labeled as good or bad credit risk.

## How It Works

1. The model and encoders are trained offline (see the training notebook/script) and saved as `.pkl` files using `joblib`.
2. `app.py` loads the trained model and encoders.
3. The user fills out a form in the browser with applicant details.
4. Categorical fields (Sex, Housing, Saving accounts, Checking account) are transformed using the saved label encoders to match the format the model was trained on.
5. The model predicts credit risk, and the result is displayed as **GOOD** or **BAD**.

## Getting Started

### Prerequisites

- Python 3.9+
- pip

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/<thomasmamaila33>/<Credit-Risk-App>.git
   cd <Credit-Risk-App>
   ```

2. (Optional but recommended) Create and activate a virtual environment:
   ```bash
   python -m venv venv
   # Windows
   venv\Scripts\activate
   # macOS/Linux
   source venv/bin/activate
   ```

3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

### Running the App

```bash
streamlit run app.py
```

The app will open automatically in your browser at `http://localhost:8501`. If it doesn't, copy that URL into your browser manually.

## Model Details

- **Algorithm:** Extra Trees Classifier (`ExtraTreesClassifier` from scikit-learn)
- **Features used:** Age, Sex, Job, Housing, Saving accounts, Checking account, Credit amount, Duration
- **Target:** Credit risk (Good / Bad)
- **Preprocessing:** Categorical features encoded with `LabelEncoder`, saved per-column as separate `.pkl` files

## Future Improvements

- Add input validation and friendlier error messages for unseen category values
- Display model confidence/probability alongside the prediction
- Add feature importance visualization
- Containerize with Docker for easier deployment
- Deploy to Streamlit Community Cloud for a live demo link

## License

This project is open source and available under the [MIT License](LICENSE).

## Acknowledgments

- Dataset: [German Credit Risk dataset](https://www.kaggle.com/datasets/uciml/german-credit) (UCI Machine Learning Repository)
- Built with [Streamlit](https://streamlit.io/) and [scikit-learn](https://scikit-learn.org/)
