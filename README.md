# ICICI Bank — CEV Option Pricing Model

### Implementation and Calibration of the Constant Elasticity of Variance (CEV) Model Using Python

## 1. Project Overview

This project implements the **Constant Elasticity of Variance (CEV)** model to price European call and put options on ICICI Bank (NSE).

Unlike the Black–Scholes model, which assumes constant volatility, the CEV model allows the volatility structure to depend on the underlying asset price. This provides a framework for examining how changes in the underlying stock price influence option pricing.

The project uses Python to implement the analytical CEV pricing formula, calibrate model parameters against observed market option prices, and evaluate the model's pricing performance.

## 2. Project Objectives

The key objectives are:

- Obtain ICICI Bank stock-price data using Yahoo Finance.
- Analyze NSE call and put option-chain data.
- Implement the analytical CEV option-pricing formula.
- Estimate the CEV model parameters using numerical optimization.
- Calculate European put prices using put–call parity.
- Compare theoretical CEV prices with observed market prices.
- Evaluate model performance using Mean Squared Error (MSE).

## 3. Mathematical Framework

The CEV model describes the underlying stock-price dynamics as:

[
dS_t = rS_tdt + \sigma S_t^{\beta/2}dW_t
]

Where:

| Parameter | Description |
|---|---|
| \(S_t\) | Underlying stock price at time \(t\) |
| \(r\) | Risk-free interest rate |
| \(\sigma\) | CEV volatility scale parameter |
| \(\beta\) | Elasticity parameter |
| \(W_t\) | Standard Brownian motion |

The instantaneous diffusion coefficient is:

\[
\sigma(S_t)=\sigma S_t^{\beta/2}
\]

The elasticity parameter \(\beta\) determines how the diffusion coefficient responds to changes in the underlying stock price.

## 4. Methodology

The project follows these steps:

**Step 1 — Market Data Collection**

Retrieve historical ICICI Bank stock-price data using Yahoo Finance and obtain the corresponding NSE option-chain data.

**Step 2 — Data Preparation**

Select the option expiry, calculate time to maturity, and prepare call and put prices across relevant strike prices.

**Step 3 — CEV Model Implementation**

Implement the analytical CEV call-pricing formula using the non-central chi-square cumulative distribution function.

**Step 4 — Put Option Pricing**

Calculate corresponding European put prices using put–call parity:

\[
P=C-S_0+Ke^{-rT}
\]

**Step 5 — Parameter Calibration**

Estimate the CEV parameters \(\sigma\) and \(\beta\) by minimizing the difference between model-generated and observed market option prices.

**Step 6 — Model Evaluation**

Compare theoretical and market option prices through graphical visualizations and Mean Squared Error.

## 5. Parameter Calibration

The model parameters are estimated through numerical optimization.

The calibration objective is to minimize the pricing error between market-observed and model-generated option prices.

The combined Mean Squared Error is:

\[
MSE =
\frac{1}{2n}
\sum_{i=1}^{n}
\left[
(C_i^{model}-C_i^{market})^2
+
(P_i^{model}-P_i^{market})^2
\right]
\]

Where:

- \(C_i^{model}\) and \(P_i^{model}\) represent theoretical call and put prices.
- \(C_i^{market}\) and \(P_i^{market}\) represent observed market call and put prices.
- \(n\) represents the number of selected strike prices.

## 6. Technology Stack

- **Programming Language:** Python
- **Data Acquisition:** yfinance
- **Numerical Computation:** NumPy
- **Data Manipulation:** Pandas
- **Statistical Distributions and Optimization:** SciPy
- **Visualization:** Matplotlib
- **Model Evaluation:** Scikit-learn
- **Development Environment:** Jupyter Notebook

## 7. Repository Structure

```text
ICICI-Bank-CEV-Option-Pricing/
│
├── ICICI_CEV_Option_Pricing.ipynb
│
└── README.md
```

The Jupyter Notebook contains the complete implementation, including data preparation, CEV pricing, parameter calibration, model evaluation, and visualizations.

## 8. How to Run the Project

### Clone the repository

```bash
git clone <GITHUB_REPOSITORY_URL>
```

### Navigate to the project directory

```bash
cd ICICI-Bank-CEV-Option-Pricing
```

### Install the required libraries

```bash
pip install numpy pandas scipy matplotlib yfinance scikit-learn jupyter
```

### Launch Jupyter Notebook

```bash
jupyter notebook
```

Open `ICICI_CEV_Option_Pricing.ipynb` and execute the cells sequentially.

## 9. Assumptions and Limitations

- The baseline model assumes European-style options.
- The initial implementation assumes zero continuous dividend yield when applying put–call parity.
- Market option prices may be affected by bid–ask spreads, liquidity, and stale last-traded prices.
- Historical volatility may differ from market-implied volatility.
- Calibration results depend on the selected expiry, strike range, market data, and optimization settings.
- A good in-sample calibration does not necessarily imply strong out-of-sample pricing performance.
- Market-data availability and redistribution are subject to the data provider's terms.

## 10. Potential Future Enhancements

- Extend calibration across multiple option expiries.
- Incorporate dividend yield into the pricing framework.
- Compare CEV and Black–Scholes pricing performance.
- Analyze implied volatility smiles and skews.
- Perform out-of-sample model validation.
- Investigate parameter stability across different market conditions.

## 11. Disclaimer

This project is developed for educational and quantitative finance research purposes only. The model outputs are not investment advice or recommendations to trade financial instruments.

---

**Author:** Reezwan Parvez

**Domain:** Quantitative Finance | Derivatives Pricing | Financial Modelling | Python
