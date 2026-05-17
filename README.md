# Project Cycle 3: Two-Sample Inference 

## Group Information 
* **Group Number**: 17
* **Members**: 113370450蘇孟孜、111370231吳子漢

## 1. Research Question & Dataset / 研究題目與資料集
* [cite_start]**Selected Question / 選定題目**: Question 5: Gender and Height/第五題：性別與身高關係 [cite: 67]
* **Research Question Formulation / 研究問題陳述**: Is the mean height different between male and female students? [cite_start]/ 男女高中生的平均身高是否存在顯著差異？ [cite: 68]
* **Dataset Source / 資料集來源**: Center for Disease Control and Prevention (CDC) - Youth Risk Behavior Surveillance System (YRBSS) 2007 dataset (`YRBS_2007.csv`). [cite_start]/ 美國疾病管制與預防中心 (CDC) 之 2007 年青少年危險行為調查數據庫 (`YRBS_2007.csv`) [cite: 2, 4, 126]。

## 2. Variable Definitions & Grouping Baseline / 變數定義與分組基準
### 2.1 Group / Independent Variable (分組變數 / 獨立變數)
* [cite_start]**Original Variable / 原始欄位**: `q2` [cite: 69]
* [cite_start]**Processed Variable / 清洗後欄位**: `Gender_Label` [cite: 69]
* [cite_start]**Data Type / 資料型態**: Categorical / Binary (類別變數 / 二元二分變數) [cite: 112]。
* **Grouping Baseline / 分組與對照基準**:
  * **Group 1 (Female / 女性群組)**: $n_1 = 6,490$ rows. Defined as the baseline group for biological sex profile. [cite_start]/ 樣本數 6,490 筆。在生理性別比較中作為基礎參照群體 [cite: 105, 198]。
  * **Group 2 (Male / 男性群組)**: $n_2 = 6,572$ rows. Defined as the comparison independent group. [cite_start]/ 樣本數 6,572 筆。定義為獨立的對照群體 [cite: 105, 198]。
### 2.2 Response / Dependent Variable (反應變數 / 依變數)
* [cite_start]**Original Variable / 原始欄位**: `q3` [cite: 70]
* [cite_start]**Processed Variable / 清洗後欄位**: `Mean Height` [cite: 70]
* [cite_start]**Data Type / 資料型態**: Continuous / Quantitative (連續變數 / 數值型反應變數) [cite: 111]。
* [cite_start]**Unit of Measurement / 計量單位**: Meters (m) / 公尺 (m) [cite: 70]。
* **Data Exclusions / 異常值剔除基準**: Raw invalid code `9.99` is strictly treated as a missing value and filtered out via listwise deletion to eliminate reporting bias. [cite_start]/ 原始問卷中的無效代碼 `9.99` 一律嚴格視為缺失值，並透過完全刪除法予以剔除，以防範填報偏誤 [cite: 264]。

## 3. Data Cleaning Summary / 資料清洗與最終樣本量
To ensure statistical validity and prevent dirty data from distorting the inferential results, listwise deletion was automatically executed across the primary variables. [cite_start]/ 為確保統計推論的有效性、防範髒資料干擾檢定結果，本分析針對核心欄位自動執行完全刪除法 [cite: 23, 264]。
* [cite_start]**Total Valid Sample Size / 有效總樣本量**: **13,062 rows / 筆** [cite: 198]
  * [cite_start]**Female Group / 女性群組**: 6,490 rows / 筆 [cite: 198]
  * [cite_start]**Male Group / 男性群組**: 6,572 rows / 筆 [cite: 198]

## 4. Statistical Methodology / 統計方法與假設檢定
* [cite_start]**Selected Method / 選用方法**: **Welch's Two-Sample t-test (異質變異數兩樣本 t 檢定)** [cite: 34, 184]
* **Method Justification / 方法選擇依據**: 
  The response variable (height) is quantitative. Following the guiding principles for Project Cycle 3, Welch's t-test is utilized by default to compare two population means unless equal variances are reasonably justified. Since the sample variances of height between male and female students are mathematically unequal, Welch's t-test is applied to dynamically correct the degrees of freedom and ensure robust inference. [cite_start]/ 反應變數（身高）屬於數值型連續變數。根據指導原則，在比較兩組平均數時，預設優先使用 Welch's t-test，而不假設兩組母體變異數相等。本分析透過 Welch's 公式進行自由度修正，以有效防範變異數相異所帶來的統計偏誤 [cite: 34, 41, 43, 111, 131]。
* **Assumption Verification / 統計假設評估摘要**:
  1. **Independence / 獨立性**: Satisfied. Data is drawn from a random national survey, and the two gender cohorts are mutually exclusive. [cite_start]/ 通過。數據源自隨機抽樣調查，且男女兩個群體相互排斥，滿足獨立樣本假設 [cite: 126]。
  2. **Measurement Scale / 測量尺度**: Satisfied. Height is measured on a continuous quantitative scale. [cite_start]/ 通過。反應變數為連續數值，符合 t 檢定要求 [cite: 111, 127]。
  3. **Normality / 常態性**: Satisfied via the Central Limit Theorem (CLT) due to the extremely large sample sizes ($n_1, n_2 > 30$). [cite_start]/ 通過。基於兩組樣本量極大，根據中央極限定理 (CLT)，樣本平均數之抽樣分佈趨近於常態分佈 [cite: 128]。
  4. **Variance Homogeneity / 變異數同質性**: Not assumed; directly accommodated using Welch's degrees of freedom adjustment. [cite_start]/ 不假設相等；直接透過 Welch's 異質變異數修正公式調整自由度進行防範 [cite: 130, 131]。

## 5. Key Results & Final Inference / 核心統計結果與最終推論
* [cite_start]**Significance Level / 顯著水準 ($\alpha$)**: 0.05 [cite: 204]
* [cite_start]**Test Statistic / 檢定統計量 ($t$)**: [請填入你們跑出來的 t 值，例如: 92.31] [cite: 202]
* [cite_start]**p-value / 顯著性檢定值**: < 0.001 [cite: 203]
* [cite_start]**Estimated Group Difference / 估計平均差距 ($\overline{x}_{\text{male}} - \overline{x}_{\text{female}}$)**: [請填入兩組身高的實際差距，例如: 0.128 m] [cite: 117, 200]

### Final Conclusion / 最終結論:
At a significance level of $\alpha = 0.05$, the null hypothesis is rejected due to the extremely small p-value ($p < 0.001$). There is overwhelming statistical evidence to conclude that the mean height is significantly different between male and female high school students. Contextually, male students are significantly taller on average than female students. 
[cite_start]在 $\alpha = 0.05$ 的顯著水準下，由於 p-value 極小 ($p < 0.001$)，故拒絕虛無假設。統計結果提供強烈證據顯示，美國男女高中生的平均身高存在高度顯著差異，且在實際脈絡中，男性的平均身高顯著高於女性 [cite: 204, 205, 262]。
