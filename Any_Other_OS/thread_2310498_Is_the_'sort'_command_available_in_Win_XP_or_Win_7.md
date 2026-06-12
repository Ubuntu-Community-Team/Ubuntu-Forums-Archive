---
title: "Is the 'sort' command available in Win XP or Win 7?"
date: 2016-01-19
forum: Any Other OS
---

### Post by vasa1 on 2016-01-19
In *sort -t/ -k 2 bdays*, *-t/* sets "/" as the delimiter and *-k 2* tells *sort* to sort the file *bdays* by the second column.

Does something equivalent exist in Win XP or Win 7?

---

### Post by SeijiSensei on 2016-01-19
According to "help sort" in cmd.exe, you can specify a column to sort on, but not a field.  So there is no equivalent to the POSIX "-t" switch in Windows sort.

---

### Post by vasa1 on 2016-01-19
@SeijiSensei, thanks for replying. I took a look at [https://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/sort.mspx](https://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/sort.mspx) and didn't find mention of sorting by columns or defining delimiters :( but there is this:
```
/+n : Specifies the character position number, n, at which sort begins each comparison.
```
I don't know how that works, but I'll ask my friend (on MS Windows) to check that option.

He wants to sort a list of names and birthdays with the dates in dd/mm/yyyy format so that sorting is by "mm". He couldn't find an easy way to do that in Excel and I don't know how that do that in Calc unless the single column with dd/mm/yyyy information is split into three columns. Then I looked at "sort".

---

