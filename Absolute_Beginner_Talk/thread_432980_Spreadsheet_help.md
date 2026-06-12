---
title: "Spreadsheet help"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by a.v.l on 2007-05-04
Yahoo groups has a poll option on the each home page which allows questions to be asked of members.  It allows for a multi- choice question to be made  and shows the numbers of votes registered against each question down one column.  To the right of this column is registered a percentage figure that each votes represents out of the total number of votes.  

Can I create something similar in Open Office spreadsheet and if so how?

---

### Post by jkblacker on 2007-05-04
Set the spreadsheet up as follows:
Column A - answers to the question on each line. For now we will assume 5 different answers.
Column B - number of people answering for this question. Say you've asked 100 people, with 20 people per answer (again, keeping the numbers simple here).
Column C - this will be our percentages, to which I will come back in a second.

At the bottom of column B, we add up the number of respondents (not strictly necessary, but in case of nasty numbers of respondents!). In B6 we type:
```
=SUM(B1:B5)
``` 
This adds up the numbers in cells B1 to B5, and will display 100.
In C1 now, we put:
```
=B1/B6*100
```
This takes the value in C1, divides it by the number of respondents and multiplies by 100 to give a percentage - in this case, 20%.
Repeat for each cell, changing B1 to B2 and so on.

I hope this helps! 

[If you were looking to do this from a website, I'm not sure, but it would probably be a case of setting up a database that collects the answers somehow, and prints the number of respondents into the spreadsheet/a report, but that's really *not* my strongpoint!]

---

### Post by a.v.l on 2007-05-04
> **jkblacker said:**
> Set the spreadsheet up as follows:
Column A - answers to the question on each line. For now we will assume 5 different answers.
Column B - number of people answering for this question. Say you've asked 100 people, with 20 people per answer (again, keeping the numbers simple here).
Column C - this will be our percentages, to which I will come back in a second.

At the bottom of column B, we add up the number of respondents (not strictly necessary, but in case of nasty numbers of respondents!). In B6 we type:
```
=SUM(B1:B5)
``` 
This adds up the numbers in cells B1 to B5, and will display 100.
In C1 now, we put:
```
=B1/B6*100
```
This takes the value in C1, divides it by the number of respondents and multiplies by 100 to give a percentage - in this case, 20%.
Repeat for each cell, changing B1 to B2 and so on.

I hope this helps! 

[If you were looking to do this from a website, I'm not sure, but it would probably be a case of setting up a database that collects the answers somehow, and prints the number of respondents into the spreadsheet/a report, but that's really *not* my strongpoint!]


Excellent, much appreciated will try it later.

---

### Post by jkblacker on 2007-05-04
Update: Playing around a little more (I'm used to Excel), you can get it to display the % sign after your answers by selecting cells C1-C5 and right clicking, and choosing 'Format Cells'. (However, you now do not need to input '*100' in the formulae, or you'll get strange answers with extra 0s like 2300% - see attachment for new format!). In this menu you can also change the number of decimal places displayed and so on.

---

### Post by a.v.l on 2007-05-04
> **jkblacker said:**
> Update: Playing around a little more (I'm used to Excel), you can get it to display the % sign after your answers by selecting cells C1-C5 and right clicking, and choosing 'Format Cells'. (However, you now do not need to input '*100' in the formulae, or you'll get strange answers with extra 0s like 2300% - see attachment for new format!). In this menu you can also change the number of decimal places displayed and so on.

Thanks very much your image help a lot.

---

