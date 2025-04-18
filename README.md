Virat Kohli Dashboard Power BI

**Cricket is a game of numbers—and what better way to analyze King Kohli’s legendary career than through the lens of data visualization?** 🚀  

This interactive Power BI dashboard captures the essence of Virat Kohli’s phenomenal journey, revealing patterns, key milestones, and performance metrics that define his career.

---

## 📌 Key Insights at a Glance

- ✅ **516 Matches** | **24K Runs** | **45.95 Avg** | **77 Centuries** | **129 Fifties**
- 🏏 Dominant performances against: 🇦🇺 **Australia**, 🏴 **England**, 🇱🇰 **Sri Lanka**, 🇿🇦 **South Africa**
- 📈 **Runs per year** trend peaking between **2016–2019**
- 📊 **Batting Average** consistently high, with standout years crossing **60+**
- 🏟️ Kohli shines at stadiums like **Wankhede**, **Kolkata**, **Adelaide**, and **Mirpur**

---

## 💡 What This Dashboard Tells Us

- Kohli has been a relentless run-machine, adapting seamlessly across formats, venues, and bowling attacks.
- His dominance in high-stakes games, particularly against top teams like Australia and England, is unmatched.
- The recent decline in his form (as seen in runs per year & average) prompts deeper analysis — is it a dip or a role shift? 🤔

This project bridges the world of **Cricket & Data Science**—showcasing how player performance can be visualized and understood with clarity and depth.

---

Measurements
-------------------------------------------------------------

Columns for 100s,50s,30+

-------------------------------------------------------------

100s = 
VAR res = SWITCH(TRUE(),
    'Virat_Kohli'[runs]>=100 && 'Virat_Kohli'[runs]<200, 1,
    'Virat_Kohli'[runs]>=200 && 'Virat_Kohli'[runs]<300, 2,
    'Virat_Kohli'[runs]>=300 && 'Virat_Kohli'[runs]<400, 3,
    0)
RETURN res

-------------------------------------------------------------

50s = 
VAR res = SWITCH(TRUE(),
    'Virat_Kohli'[runs]>=50 && 'Virat_Kohli'[runs]<99, 1,
    'Virat_Kohli'[runs]>=150 && 'Virat_Kohli'[runs]<199, 1,
    'Virat_Kohli'[runs]>=250 && 'Virat_Kohli'[runs]<299, 1,
    0)
RETURN res

---------------------------------------------------------------

30+ = IF('Virat_Kohli'[runs]>=30, 1, 0)

---------------------------------------------------------------

Calender Columns

---------------------------------------------------------------
|||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||

Create Date Table :->

---------------------------------------------------------------

Step 1:  

Calender = CALENDAR(
        DATE ( YEAR ( MIN(Virat_Kohli[date]) ),1,1), 
        DATE(YEAR(MAX(Virat_Kohli[date])),12,31)
)

---------------------------------------------------------------

Step 2: 

Month , year , Day Column Measures

---------------------------------------------------------------

Step 3: 

day = FORMAT(Calender[Date],"ddd")

day_no = DAY(Calender[Date])

month = FORMAT(Calender[Date],"mmm")

month_no = MONTH(Calender[Date])

year = YEAR(Calender[Date])

||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||
----------------------------------------------------------------


100s = SUM(Virat_Kohli[100s])

30+ = SUM(Virat_Kohli[30+])

50s = SUM(Virat_Kohli[50s])

HighestScore = MAX(Virat_Kohli[runs])

Runs = SUM(Virat_Kohli[runs])

Total_Matches = COUNT(Virat_Kohli[opponent]) 








