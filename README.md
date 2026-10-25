# Water Resource Forecasting and Management Project

## Project Overview

This project presents a data-driven framework for forecasting and managing water resources in the Tangier region. It combines:

- multivariate LSTM forecasting,
- sectoral demand analysis,
- water stress evaluation,
- policy scenario simulation,
- and Model Predictive Control (MPC) for water allocation.

The objective is not only to predict future water demand, supply, and storage, but also to support decision-making under different management strategies.

---

## Project Structure

### `data/`
This folder contains the datasets used in the project.

- **`tangier_synthetic_water_model_with_supply_2000_2035.csv`**  
  Main baseline dataset used for the core forecasting model.

- **`tangier_synthetic_water_model_with_supply_FIXED_STORAGE_2000_2035.csv`**  
  Corrected version of the dataset where storage is reconstructed/fixed for physically consistent modeling.

- **`tangier_synthetic_water_virtual_water_2000_2035.csv`**  
  Scenario dataset representing the *virtual water* policy, where water-intensive goods are imported to reduce local water demand.

- **`tangier_synthetic_water_food_self_sufficiency_2000_2035.csv`**  
  Scenario dataset representing the *food self-sufficiency* policy, which increases local agricultural production and therefore raises water demand.

---

## Main Files

### `final_lstm_forecasting.ipynb`
This is the **main notebook of the project**.

It includes:
- loading and preprocessing the main dataset,
- scaling the variables,
- creating time-series sequences,
- building the multivariate LSTM model,
- training and validating the model,
- forecasting:
  - domestic demand,
  - agricultural demand,
  - industrial demand,
  - total supply,
  - storage,
- evaluating the model using MAE and RMSE,
- and generating the main plots used in the report.

This notebook should be considered the **core forecasting pipeline**.

---

### `fixed_dataset.ipynb`
This notebook is used to **prepare and correct the dataset**, especially the storage variable.

Its purpose is to:
- inspect inconsistencies in the original synthetic dataset,
- reconstruct or fix storage values,
- ensure physical coherence between demand, supply, and storage,
- and produce a cleaner dataset for model training.

This notebook is important because storage is a cumulative hydrological variable and must remain physically meaningful before being used in the forecasting model.

---

### `lstm_policy_scenarios.ipynb`
This notebook is dedicated to **policy scenario analysis**.

It uses alternative datasets to study how different strategies affect water demand and system behavior:
- baseline scenario,
- virtual water scenario,
- food self-sufficiency scenario.

It includes:
- loading scenario-specific datasets,
- applying the forecasting framework to each scenario,
- comparing prediction performance,
- analyzing how policy choices affect demand patterns,
- and generating the scenario comparison figures and metrics used in the report.

This notebook is used for the **Policy Scenario Analysis** section.

---

### `final_forecast_2026_2035.csv`
This file contains the final forecast outputs for the period **2026–2035**.

It is used as a summary output of the forecasting process and may include predicted values such as:
- sectoral demand,
- total supply,
- storage,
- and other derived indicators.

This file can be used for result inspection without rerunning the notebooks.

---

## Recommended Reading Order

To understand the project clearly, the notebooks should be reviewed in the following order:

1. **`fixed_dataset.ipynb`**  
   To understand how the dataset was cleaned and how storage was reconstructed.

2. **`final_lstm_forecasting.ipynb`**  
   To understand the main LSTM forecasting pipeline and the baseline results.

3. **`lstm_policy_scenarios.ipynb`**  
   To understand how alternative policy scenarios were simulated and compared.

---

## Main Outputs of the Project

The project produces the following main outputs:

- forecasts of domestic, agricultural, and industrial demand,
- total supply forecasting,
- storage forecasting,
- water stress analysis,
- scenario comparison,
- and water allocation analysis using MPC.

---

## Notes for the Reader

- The datasets are synthetic but designed to reflect realistic temporal behavior.
- Storage was reconstructed to improve physical consistency.
- The project combines both **prediction** and **decision support**:
  - LSTM provides the forecasts,
  - MPC uses those forecasts for allocation decisions,
  - scenario analysis evaluates the impact of policy changes.

---

## Author

**Yousra Amami**  
Master's Degree in Artificial Intelligence and Data Sciences  
Faculty of Sciences and Techniques, Tangier  
Abdelmalek Essaadi University

Supervised by: **Prof. Mostapha Ezziyyani**