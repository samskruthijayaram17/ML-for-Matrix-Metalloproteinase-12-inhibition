# Bioactivity Prediction for Matrix Metalloproteinase 12 (MMP-12)

A machine learning project for predicting bioactivity (pIC50) of compounds against Matrix Metalloproteinase 12 using molecular descriptors and regression models.

## Project Overview

This project uses data from the ChEMBL database to build predictive models for bioactivity against MMP-12, a protein target involved in various biological processes. The project encompasses data collection, exploratory analysis, feature engineering, model development, and an interactive prediction application.

## Project Structure

```
mini project/
├── scripts/              # Jupyter notebooks for analysis and modeling
├── data/                 # Raw and processed datasets
├── plots/                # Visualization outputs and statistical results
└── README.md             # This file
```

## Scripts

All analysis and modeling workflows are implemented as Jupyter notebooks:

### 1. **data collection.ipynb**
   - Queries ChEMBL database for Matrix Metalloproteinase 12 bioactivity data
   - Filters IC50 measurements for active/inactive/intermediate classification
   - Extracts molecule SMILES notation
   - Outputs: `bioactivity_data.csv`, `bioactivity_preprocessed_data.csv`

### 2. **data analysis.ipynb**
   - Exploratory data analysis of bioactivity data
   - Statistical analysis of compound properties
   - Distribution plots and correlation analysis
   - Class imbalance assessment

### 3. **descriptor dataset preparation.ipynb**
   - Calculates molecular descriptors using PaDEL (Padua Descriptor Library)
   - Computes 2D/3D fingerprints and physicochemical properties
   - Prepares feature matrix for machine learning
   - Outputs: `descriptors_output.csv`

### 4. **regression random forest.ipynb**
   - Builds Random Forest regression model
   - Hyperparameter optimization
   - Model training and evaluation
   - Generates `Matrix Metalloproteinase 12_model.pkl` for the web app

### 5. **compare regressor.ipynb**
   - Compares multiple regression algorithms (Random Forest, Gradient Boosting, SVM, etc.)
   - Cross-validation and performance metrics
   - Model selection and benchmarking

## Data

### Raw Data
- **bioactivity_data.csv**: Complete ChEMBL IC50 data for MMP-12
  - Contains: molecule ID, SMILES, IC50 values, experimental conditions

- **bioactivity_data_3class_pIC50.csv**: Classified bioactivity data
  - Active (pIC50 ≥ 6)
  - Inactive (pIC50 < 5)
  - Intermediate (5 ≤ pIC50 < 6)

### Processed Data
- **bioactivity_preprocessed_data.csv**: Cleaned bioactivity data with classifications
  - Removed missing values
  - Added bioactivity class labels
  - Standardized IC50 to pIC50 (negative log IC50)

- **descriptors_output.csv**: Calculated molecular descriptors
  - 100+ physicochemical features
  - 2D and 3D fingerprints
  - Ready for machine learning input

- **molecule.smi**: SMILES notation for all compounds
  - Input format for descriptor calculation

### Bioactivity Data Files
- **bioactivity_data_3class_pIC50_pubchem_fp.csv**: Data with PubChem fingerprints
  - Used for model training and evaluation

## Plots and Results

Generated visualizations and statistical analyses:

### Distribution Plots
- `plot_bioactivity_class.pdf` - Distribution of active/inactive/intermediate compounds
- `plot_ic50.pdf` - IC50 value distribution
- `plot_LogP.pdf` - Lipophilicity (LogP) distribution
- `plot_MW.pdf` - Molecular weight distribution
- `plot_NumHAcceptors.pdf` - Hydrogen bond acceptors distribution
- `plot_NumHDonors.pdf` - Hydrogen bond donors distribution
- `plot_MW_vs_LogP.pdf` - MW vs LogP correlation scatter plot

### Statistical Tests
- `mannwhitneyu_*.csv` - Mann-Whitney U test results comparing active vs inactive compounds
  - Tests for significant differences in molecular properties

## Installation & Requirements

### Dependencies
- pandas 1.1.3
- streamlit 0.71.0
- scikit-learn (for model training)
- RDKit (for chemistry operations)
- PaDEL-Descriptor (for molecular descriptor calculation)
- chembl_webresource_client (for data retrieval)
- matplotlib, seaborn (for plotting)


## Key Findings

- Significant differences in molecular properties between active and inactive compounds
- Lipophilicity (LogP) and molecular weight are important predictive features
- Random Forest outperforms other regression models for this target
- Model can rank-order compounds by predicted bioactivity

## Biological Context

**Matrix Metalloproteinase 12 (MMP-12)**:
- Also known as macrophage elastase
- Involved in ECM remodeling and inflammation
- Potential drug target for inflammatory diseases
- Target validated for drug discovery efforts

## Files Generated During Execution

The scripts generate the following output files:
- `descriptors_output.csv` - Molecular descriptors (created when app.py is run)
- `prediction.csv` - Batch prediction results (downloaded from app)
- `Matrix Metalloproteinase 12_model.pkl` - Trained model (in app/ folder)

## Future Improvements

- Deep learning models (neural networks) for improved predictions
- Multi-task learning with related protease targets
- Uncertainty quantification in predictions
- Explainability analysis (SHAP values) for feature importance
- Cross-validation with external test sets

## References

- ChEMBL Database: https://www.ebi.ac.uk/chembl/
- RDKit: Open-source chemistry toolkit
- PaDEL-Descriptor: Descriptor calculation tool
- Scikit-learn: Machine learning library

## Author Notes

This project demonstrates end-to-end machine learning workflow in drug discovery:
1. **Data Acquisition** - Leveraging public bioactivity databases
2. **Data Exploration** - Understanding molecular property distributions
3. **Feature Engineering** - Calculating relevant molecular descriptors
4. **Model Development** - Training and comparing regression models

## License

Project data sourced from ChEMBL (CC0 license).


