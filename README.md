# German power merit order 2026

A simplified hourly merit-order model of the German power market, 1 January to 12 November 2026, built for an interview task. For every hour it works out a model power price and the fuel that set it, and it tracks how much gas the gas plants burned.

## Main finding

Gas set the model price in about half of all hours. But as gas got more expensive it fell behind coal and lignite in the merit order. Between January and October the model base price rose from €101 to €139/MWh, while gas burn fell from 61 to 26 mcm/d. So how often gas sets the power price says little about how much gas is actually burned.

## Files

| File | What it is |
|---|---|
| `merit_order.ipynb` | The analysis, from the raw data to the answers |
| `Answers.pdf` | One-page note answering the five questions in the brief |
| `InterviewTask_brief.pdf` | The task brief |
| `data/data/` | Input data supplied with the task |
| `outputs/` | Tables and charts the notebook saves |
| `requirements.txt` | Python packages |

## How to run

Python 3.10:

```
pip install -r requirements.txt
jupyter nbconvert --to notebook --execute merit_order.ipynb --output merit_order.ipynb
```

Or open the notebook in Jupyter or VS Code and run all cells. It reads the CSVs from `data/data/` and writes everything to `outputs/`. Checks run throughout, so it stops if the data isn't what the model expects.

## My assumptions

- Lignite fuel cost: €2.9/MWh thermal (DIW Data Documentation 68). Tested from 0 to 20.
- Hours when must-run and renewables cover demand are priced at €0.
- Hours when demand is above all available capacity are priced at the most expensive plant's cost.
- A day's price-setting fuel is the one marginal in the most hours.

## AI use

I used an AI assistant to help write and check the Python code, following a workflow and checklist I set. I chose the assumptions, checked the results and wrote the note myself.
