# SAARTHI

**System for Automated Analysis of pRojects and Technologies for Holistic Insights**

A dashboard I built during my internship at the Business Development Group (BDG) of CSIR-National Physical Laboratory, New Delhi. It takes the group's project and technology transfer records, which are kept in Excel workbooks, and turns them into KPIs, charts and a searchable view of every record.

![Dashboard home](images/04-dashboard-home.png)

## A note on the data and code
This was done as part of a government internship, so the source workbooks and the application code are not published here. The repository only contains screenshots of the dashboard. Any figures or IDs visible in them come from the internal records and are shown only to illustrate how the tool works.

## What it does
1. **Reads the workbook.** The user uploads the BDG Excel file and picks a sheet. SAARTHI handles the four project sheets (TSP, CNP, CLP, SSP) and the technology transfer (TT) sheet.
2. **Cleans and converts the data.** The raw sheets are not analysis-ready: some records spill over onto continuation rows and amounts are written as text, for example "Rs 2.5 Lakhs". A conversion step turns each sheet into one clean table with proper dates and numbers.
3. **Validates before opening the dashboard.** A check lists missing values by column along with the record IDs affected, and the dashboard stays locked until it has been run.
4. **Shows the dashboard.** Six KPI cards sit at the top, followed by six analysis sections. Each section has 7 to 8 charts covering project overview, financial summary, closure and deadlines, revisions, clients and divisions.
5. **Lets you search the records.** A single search box takes conditions such as `date = 22-12-2021`, `st = delhi` or `cost > 500000`. Conditions can be combined, listed or chained (see below).
6. **Exports to Excel.** The records that match a search can be exported as a formatted .xlsx file, with the conditions used written at the top and the columns chosen by the user.

## Screenshots

| Upload | Sheet selection |
|---|---|
| ![Upload screen](images/01-upload-screen.png) | ![Sheet selection](images/02-sheet-selection.png) |

![Data validation](images/03-data-validation.png)

### Search
The search box understands short column names and a few operators.

| Symbol | Meaning |
|---|---|
| `=` `!=` `<` `>` `<=` `>=` | comparison |
| `,` | several values for one column, e.g. `state = delhi,haryana` |
| `;` | AND, e.g. `state = delhi ; cost > 500000` |
| `.` | narrow the previous result, e.g. `state = delhi ; cost > 500000 . pi = sharma` |

![Search](images/05-lookup.png)

### Excel export
![Excel export](images/06-excel-export.png)

The full set of screenshots is also available as a PDF in [`docs/`](docs/Dashboard-Screenshots.pdf).

## Tools
- Python (pandas, openpyxl, Plotly, Dash)
- SQL
- Excel (.xls / .xlsx) for input and output

## Repository layout

```
.
├── docs/        screenshots as a PDF
├── images/      dashboard screenshots
└── README.md
```

## Author
Yash Rana
