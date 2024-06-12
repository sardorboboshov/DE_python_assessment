# Feature Engineering Decisions

This document outlines the decisions made during the feature engineering process. These decisions may be adjusted based on future business requirements.

## 0. Dropping rows
  - **Dropped rows without any contracts**:
    - **Current Implementation**: Since rows without contracts don't add any value to feature, they are dropped.

- **Dropped rows with duplicate contracts**:
    - **Current Implementation**: Some rows have same contracts (with same contract_id and claim_id), 
    which means they need to be dropped. 

## 1. Feature: `tot_claim_cnt_180d`

- **Calculation Period**:
  - **Current Implementation**: Last 180 days counted from today.
  - **Alternative**: Last 180 days counted from `application_date`.

- **Technical Meaning of 'No Claims'**:
  - **Definition**: There is no single claim date which is non-null.

## 2. Feature: `disb_bank_loan_wo_tbc`

- **Technical Meaning of 'No Claims'**:
  - **Definition**: There is no single `contract_date` which is non-null.

- **Technical Meaning of 'No Loans'**:
  - **Definition**: There are valid claims, but the sum of `loan_summa` is `0`.

## 3. Feature: `day_sinlastloan`

- **Technical Meaning of 'No Claims'**:
  - **Definition**: There is no single `contract_date` which is non-null (consistent with the previous feature).

- **Technical Meaning of 'No Loans'**:
  - **Definition**: There are valid claims, but the sum of `summa` is `0`.
