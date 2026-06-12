# NHS Acute Discharge Delays Analysis (2025–2026)

## Project Overview

This project analyses NHS England Acute Daily Discharge Situation Report data for the 2025–26 financial year.

The analysis focuses on acute discharge delays, including patients who no longer meet the criteria to reside, patients discharged, patients remaining in hospital, additional bed days lost, discharge destinations and delay reasons.

This project forms Phase 3 of a wider NHS operational analytics portfolio:

1. NHS A&E Patient Flow Analysis
2. NHS Bed Availability & Occupancy Analysis
3. NHS Acute Discharge Delays Analysis

Together, these projects explore different parts of the hospital patient-flow pathway: urgent and emergency care demand, inpatient bed capacity, and discharge flow out of hospital.

## Project Objectives

The objectives of this project were to:

* Analyse national acute discharge delay trends across 2025–26.
* Identify changes in patients who no longer meet the criteria to reside.
* Analyse patients discharged and patients remaining in hospital after no longer meeting criteria to reside.
* Explore regional, ICB and provider-level variation in discharge delays.
* Analyse additional bed days lost linked to delayed discharge.
* Examine discharge destinations and delay reasons.
* Prepare clean Tableau-ready datasets for dashboard development.

## Dataset

The project uses NHS England Acute Daily Discharge Situation Report monthly CSV files for the 2025–26 financial year.

The files cover:

* April 2025 to March 2026
* National, regional, ICB and provider-level reporting
* Daily discharge activity
* Weekly snapshot metrics
* Discharge destination information
* Delay reason information

The dataset is provided in long format, with each row representing a reporting period, geography level, organisation, metric and value.

## Tools Used

* Python
* Pandas
* NumPy
* Matplotlib
* Jupyter Notebook
* Tableau Public
* GitHub

## Data Cleaning and Validation

The raw dataset contained 429,408 rows across 12 monthly CSV files.

A data quality review was completed before analysis. The main issues identified were:

* April and June files contained `01/10/2025` rows under `Delay reason LOS 7+`. These were retained and flagged as corrected CSV date-label issues because the values matched the relevant monthly publication structure.
* The June file contained 168 out-of-month NCTR rows dated `01/05/2025` with placeholder values. These were excluded from the cleaned dataset.
* Weekly boundary dates from the previous month were retained where appropriate because they related to weekly snapshot reporting.
* Cost-related delay reason rows were retained separately but excluded from the main patient-count analysis.

After cleaning, the final analytical dataset contained 429,240 rows.

## Analysis Structure

The notebook is structured around the following areas:

1. Data loading and validation
2. Data cleaning and preparation
3. National discharge-flow trends
4. Regional discharge delay analysis
5. ICB-level analysis
6. Provider-level analysis
7. Additional bed days lost
8. Delay reason analysis
9. Discharge destination analysis
10. Tableau-ready output preparation

## Key Findings

### National Discharge-Flow Trends

Nationally, a large proportion of patients who no longer met the criteria to reside remained in hospital during 2025–26.

The national NCTR not-discharged rate increased from 55.8% in Q1 to 59.2% in Q4. During the same period, the average daily number of patients who no longer met the criteria to reside increased, while the average daily number discharged decreased.

This suggests that discharge-flow pressure became more pronounced toward the end of the financial year.

### Regional Variation

Discharge-flow pressure was not evenly distributed across NHS England regions.

Across the full financial year, the South East had the highest annual NCTR not-discharged rate, followed by the North West and South West. In Q4, several regions had not-discharged rates above 60%, including the South East, North East and Yorkshire, North West and London.

### ICB-Level Variation

ICB-level analysis showed further variation within and across regions.

NHS Sussex Integrated Care Board had the highest annual NCTR not-discharged rate among ICBs, followed by NHS Northamptonshire Integrated Care Board and NHS Lincolnshire Integrated Care Board.

### Provider-Level Variation

Provider-level analysis showed substantial variation across NHS acute providers.

To support fairer comparison, provider-level rankings were restricted to organisations with at least 300 reporting days and at least 10,000 NCTR patients during 2025–26. This excluded one provider with limited reporting coverage.

Among included providers, Northern Care Alliance NHS Foundation Trust had the highest NCTR not-discharged rate.

These findings should be interpreted carefully. A high not-discharged rate does not necessarily indicate poorer clinical performance; it may reflect case mix, local discharge pathway capacity, social care availability, reporting practices and wider system pressures.

### Additional Bed Days Lost

Additional bed days lost provide a capacity-impact view of discharge delays.

The dataset includes weekly snapshot metrics for patients with length of stay of 7 days or over, 14 days or over, and 21 days or over. These categories are overlapping, so they were not summed together for provider ranking.

The main bed-days analysis used the LOS 7+ metric as the headline measure.

At national level, the LOS 7+ additional bed days metric recorded more than 6.7 million additional bed days across 2025–26.

### Delay Reasons

Delay reason analysis showed that the largest LOS 7+ delay reason category was Capacity, followed by Interface process and Hospital process.

The leading delay reasons included:

* Waiting for confirmation of immediate care needs and pathway
* Bed-based rehabilitation, reablement or recovery services not yet available
* Awaiting therapy review of need for supported discharge
* Residential or nursing home care not yet available
* Residential or nursing home care arrangements still underway

This suggests that acute discharge delays were shaped by both internal hospital processes and wider system constraints, including rehabilitation, reablement, residential and nursing home care, community services and care transfer processes.

### Discharge Destinations

Discharge destination analysis showed that most recorded discharges were through Pathway 0.

Pathway 0 discharge to a domestic home, hotel or temporary accommodation without the need for new or increased support accounted for 83.3% of recorded discharge destinations nationally.

More complex discharge pathways, including Pathway 1, Pathway 2 and Pathway 3, accounted for a smaller share of recorded discharge destinations.

## Tableau Dashboard

A Tableau dashboard was prepared using cleaned Tableau-ready CSV outputs.

The dashboard is designed around four main sections:

1. National overview

   * NCTR patients
   * NCTR discharged rate
   * NCTR not-discharged rate
   * Monthly and quarterly trends

2. Geographic variation

   * Region, ICB and provider comparisons
   * NCTR not-discharged rate
   * NCTR discharged rate

3. Capacity impact

   * LOS 7+ additional bed days
   * Provider-level bed-day burden

4. Reasons and destinations

   * Delay reason categories
   * Top delay reasons
   * Discharge destination share

Tableau Public link: [NHS Acute Discharge Delays Analysis 2025–26](https://public.tableau.com/views/NHSAcuteDischargeDelaysAnalysis202526/NHSDischargeDelays?:language=en-US&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link)


## Tableau-Ready Outputs

The following Tableau-ready datasets were created:

* `tableau_national_discharge_kpis_2025_26.csv`
* `tableau_geography_discharge_summary_2025_26.csv`
* `tableau_national_los7_bed_days_monthly_2025_26.csv`
* `tableau_provider_los7_bed_days_2025_26.csv`
* `tableau_national_los7_delay_reason_categories_2025_26.csv`
* `tableau_national_los7_delay_reasons_2025_26.csv`
* `tableau_national_discharge_destinations_2025_26.csv`

## Limitations

This analysis is descriptive and does not prove causation.

Some metrics are reported as daily measures, while others are weekly snapshot measures. These were analysed separately to avoid mixing different reporting frequencies.

Additional bed days metrics for LOS 7+, LOS 14+ and LOS 21+ are overlapping categories. Therefore, they were not summed together for the main provider ranking.

Provider-level comparisons should be interpreted carefully. Differences may reflect local case mix, discharge pathway availability, social care capacity, community service provision, reporting practices and organisational context.

The dataset does not include patient-level information, clinical complexity, local operational context or detailed social care capacity data. Therefore, the analysis can identify patterns and variation but cannot fully explain the underlying reasons for all observed differences.

## Conclusion

This project analysed NHS acute discharge delays across the 2025–26 financial year, focusing on patients who no longer met the criteria to reside, NCTR discharged rates, patients remaining in hospital, additional bed days lost, delay reasons and discharge destinations.

The analysis showed that discharge-flow pressure increased toward the end of the financial year, with the national NCTR not-discharged rate rising from 55.8% in Q1 to 59.2% in Q4.

Additional bed days analysis highlighted the capacity impact of delayed discharge, with more than 6.7 million LOS 7+ additional bed days recorded nationally.

Delay reason analysis suggested that discharge delays were shaped by a combination of onward-care capacity constraints, hospital-community interface processes and internal hospital processes.

This project completes the third phase of the NHS patient-flow analytics portfolio, complementing earlier analysis of A&E performance and bed occupancy.
