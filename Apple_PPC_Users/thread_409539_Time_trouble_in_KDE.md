---
title: "Time trouble in KDE"
date: 2007-04-14
forum: Apple PPC Users
---

### Post by macminiuser on 2007-04-14
How does a person go about changing the time from 24hr to 12hr in kde?
I am useing a ppc mac mini.
Running Ubuntu 6.0.6 LTS

---

### Post by jordanmthomas on 2007-04-14
right click on your clock
go to Date Time & Format
Go to the Time and Dates tab

For Time format, put this:
```
PH:MM:SS AMPM
```
This will give you times like 05:34:10 PM if you have seconds enabled on the clock, otherwise the seconds will be left off.
If you don't like the 0 being there, put this instead:
```
pH:MM:SS AMPM
```
(it's just a lowercase p)

---

