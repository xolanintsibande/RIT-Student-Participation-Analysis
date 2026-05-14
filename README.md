# RIT Student Participation Analysis
 
Analyzed 8,558 student application records to understand why 52.8% of applicants fail to participate in educational opportunities. Built an 87% accurate machine learning model to predict engagement and deliver actionable recommendations.

---

## 📊 The Problem

Despite growing application volume across educational platforms, engagement rates remain inconsistent:
- **Overall engagement:** 47.2% (more than half of applicants never show up)
- **Internship engagement:** 21.5% (63% of applications, but massive dropout)
- **Course engagement:** 93.2% (proven format, but underutilized)
- **Event engagement:** 96.3% (highest conversion, limited availability)

This analysis identifies why and provides data-driven solutions.

---

## 🎯 What I Did

### 1. Data Cleaning & Preparation
- Standardized 5 datetime columns (parsed mixed formats, fixed timestamps)
- Handled 3,794 missing values (44.3% of dataset) without data loss
- Validated 8 status codes across 8,558 records
- Normalized institution names (resolved 7+ case variants for Saint Louis University alone)
- Result: Production-ready dataset with zero duplicates

### 2. Feature Engineering
Derived 10 predictive features from raw data:
- **days_to_apply:** Urgency metric (signup to application time)
- **Age & Age_Group:** Demographic segmentation (<18, 18-22, 23-26, 27-30, 31+)
- **Signup Day:** Day-of-week behavior patterns
- **Apply_Month & Apply_Year:** Temporal and seasonal signals
- **opp_duration_days:** Program length impact on completion
- **Acceptance_rate & Drop_rate:** Opportunity-level quality signals
- **Engaged_Flag:** Binary target variable (participated = 1, dropped = 0)

### 3. Exploratory Data Analysis
Uncovered critical patterns across 4 dimensions:

**By Category**
- Internships: 5,421 applications (63%), 21.5% participation
- Courses: 2,037 applications (24%), 93.2% participation
- Competitions: 425 applications (5%), 84.2% participation
- Events: 545 applications (6%), 96.3% participation
- Engagement: 130 applications (2%), 96.9% participation

**By Geography (71 countries)**
- High volume, low engagement: US (3,976 apps, 40%), India (2,836 apps, 49%)
- Low volume, high engagement: Egypt (78%), Kenya (74%), Pakistan (71%)
- Market insight: African learners 2x more committed than US applicants

**By Timing**
- **Early planners** (90+ days): 81% participation
- **On-time** (31-89 days): 75% participation
- **Middle window** (8-30 days): 58% participation ← Largest gap
- **Last-minute** (0-7 days): 94% participation
- **Post-start:** 94-98% participation

**By Time Period**
- Oct 2022 - July 2023: 90%+ engagement (stable growth phase)
- August 2023 onward: Sharp decline as volume surged
- January 2024 spike: 2,489 applications, engagement crashed to 31.4% (scaling failure)

### 4. Machine Learning Models
Built and compared two classification models:

**Random Forest (Primary Model)**
```
Accuracy:    86.97%
Precision:   90.0%
Recall:      81.5%
F1-Score:    85.5%
False Neg:   18.5%
```

**Logistic Regression (Baseline)**
```
Accuracy:    80.2%
Precision:   82.1%
Recall:      67.2%
F1-Score:    76.2%
False Neg:   32.8%
```

→ Random Forest selected: superior recall identifies 14% more at-risk students

### 5. Feature Importance Analysis
What matters most to engagement?

| Rank | Feature | Weight | Insight |
|------|---------|--------|---------|
| 1 | Opportunity Category | 51.5% | Program type dominates all else |
| 2 | Opportunity Name | 21.9% | Specific programs within category matter |
| 3 | Month Applied | 11.1% | Temporal patterns significant |
| 4 | Student Age | 6.1% | Slight demographic influence |
| 5 | Student Major | 4.5% | Academic field has small effect |
| 6 | Country | 2.5% | Geography minor factor |
| 7 | Day of Week | 1.9% | Nearly negligible |
| 8 | Gender | 0.7% | **Zero engagement disparity** |

**Key insight:** Program type 51x more important than gender. Opportunity design > demographic targeting.

---

## 📈 Key Findings

### Finding 1: Internship Crisis
**Challenge:** Internships attract majority of interest but convert poorest.

**Data:**
- 63% of all applications are for internships
- Yet only 21.5% actually participate
- Gap of 41.5 percentage points
- Exception: Health Care Management internship (45%) — worth replicating

**Implication:** Not a demand problem. Design/execution problem.

### Finding 2: Geographic Opportunity
**Discovery:** African and South Asian markets show exceptional commitment despite low volume.

**Data:**
| Region | Volume | Engagement |
|--------|--------|-----------|
| Egypt | 50 | 78% |
| Kenya | 38 | 74% |
| Pakistan | 219 | 71% |
| Nigeria | 760 | 57% |
| US | 3,976 | 40% |
| India | 2,836 | 49% |

**Opportunity:** Expand in high-engagement regions. Lower customer acquisition cost, higher conversion.

### Finding 3: January 2024 Scaling Failure
**Event:** Single month had 2,489 applications (5x normal volume).

**Impact:** Engagement rate collapsed from 90%+ to 31.4%.

**Diagnosis:** Platform couldn't handle surge. Quality control broke. Many low-intent applicants mixed in.

**Lesson:** Growth without infrastructure = quality loss.

### Finding 4: Middle-Window Intervention Opportunity
**Pattern:** Students applying 8-30 days before start show 58% participation.

**Context:**
- 90+ days out: 81% (committed planners)
- 0-7 days: 94% (desperate/urgent)
- 8-30 days: 58% (forgotten/cold)

**Action:** This window is where we lose most recoverable students. Targeted nudges could lift significantly.

### Finding 5: One Program Has Zero Engagement
**Anomaly:** AI Ethics Challenge (55 applicants, 0% participation).

**Model caught it:** Random Forest flagged at 3.6% predicted probability (correct diagnosis).

**Status:** Needs immediate audit. Program may be broken, cancelled, or poorly communicated.

---

## 💼 Business Impact

### Revenue Opportunity
If internship participation improves from 21.5% → 35%:
- Current: 1,165 students participating
- Potential: 1,900+ students participating
- Additional revenue at ~$16K per student: **$3.5M+**

### At-Risk Students Identified
- 4,256 students applied but didn't participate
- 2,000+ in "middle window" (8-30 days before start)
- Recoverable with targeted intervention

### Market Expansion Potential
- Egypt, Kenya, Nigeria, Pakistan show 70%+ participation
- Currently underserved (50-760 applications vs. US 3,976)
- Opportunity for localized growth with lower acquisition cost

---

## 🎯 Recommendations Delivered

### Priority 1: Fix Internship Pipeline
**Action:** Deploy 2-hour readiness module before internship placement
- **Target:** Reduce non-participation from 78.5% to below 60%
- **Timeline:** Implement within 2 weeks
- **Impact:** 750+ additional students participating

### Priority 2: Middle-Window Intervention
**Action:** Automated reminders and bridge activities for students 8-30 days before start
- **Target:** Increase participation from 58% to 75%
- **Timeline:** Immediate deployment
- **Impact:** 2,000+ affected students

### Priority 3: Urgent Program Audit
**Action:** Investigate AI Ethics Challenge (0% engagement)
- Check registration system
- Verify student communications
- Confirm program is active or cancel formally
- **Timeline:** Complete within 1 week

### Priority 4: Geographic Expansion
**Action:** Increase opportunity supply in high-engagement markets
- Focus: Egypt, Kenya, Nigeria, Pakistan
- Rationale: 70%+ participation vs. 40-50% elsewhere
- Expected ROI: Higher conversion, lower marketing cost

### Priority 5: Scale High-Performers
**Action:** Create more courses and competitions (85%+ engagement)
- Reduce emphasis on internships until redesigned
- Proven formats with lower support overhead
- Better student outcomes

---

## 📊 Dataset Overview

| Metric | Value |
|--------|-------|
| Total Records | 8,558 |
| Date Range | Oct 2022 - Mar 2024 |
| Countries | 71 |
| Opportunity Categories | 5 |
| Unique Opportunities | 22 |
| Columns (Original) | 16 |
| Columns (Engineered) | 10 additional |
| Missing Values Handled | 3,794 (44.3%) |
| Duplicates | 0 |

---

## 🎓 Methodology

**Week 1: Data Understanding**
- Loaded and inspected 8,558 records
- Validated 16 columns across all categories
- Identified data quality issues (missing dates, case variants)
- Created data dictionary with full definitions
- Status: ✅ Complete

**Week 2: Exploratory Analysis**
- Engineered 10 predictive features
- Analyzed participation patterns by category, geography, timing
- Identified inflection points and anomalies
- Discovered "middle window slump" and geographic inversion
- Status: ✅ Complete

**Week 3: Machine Learning**
- Trained Random Forest (86.97% accuracy)
- Trained Logistic Regression baseline (80.2% accuracy)
- Generated predicted probabilities for all opportunities
- Analyzed feature importance rankings
- Status: ✅ Complete

**Week 4: Strategic Insights**
- Synthesized findings into 5 actionable recommendations
- Quantified revenue opportunity ($3.5M+)
- Provided implementation roadmap
- Outlined KPI monitoring framework
- Status: ✅ Complete

---

## 📈 Results Summary

| Metric | Result |
|--------|--------|
| Model Accuracy | 86.97% (Random Forest) |
| Feature Importance (Top) | Category 51.5% |
| Engagement Range | 21.5% - 96.3% |
| Largest Gap | Internship 21.5% vs Event 96.3% |
| Revenue Opportunity Identified | $3.5M+ |
| At-Risk Students Flagged | 4,256 |
| Geographic Expansion Potential | Egypt (78%), Kenya (74%), Pakistan (71%) |
| Implementation Timeline | 4 weeks |

---

## 🔍 Key Insights at a Glance

✓ **Problem Identified:** 52.8% of applicants don't participate  
✓ **Root Cause Found:** Opportunity type matters 51x more than demographics  
✓ **High-Risk Segment:** Students applying 8-30 days before start (58% participation)  
✓ **Market Opportunity:** African learners 2x more committed than US applicants  
✓ **Revenue Potential:** $3.5M from improved internship conversion  
✓ **Model Built:** 87% accurate Random Forest for early warning system  
✓ **Recommendations:** 5 prioritized actions with implementation timelines  

---
