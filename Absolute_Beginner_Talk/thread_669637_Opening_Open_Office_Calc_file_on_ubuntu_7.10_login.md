---
title: "Opening Open Office Calc file on ubuntu 7.10 login"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by no3 on 2008-01-16
How do I make an open office calc file open up whenever I login to Ubuntu?

 I've tried sessions, but that seems to work for applications only, not for files.
 I use this .ods file to keep track of the hours I spend at work, so it is very important that I keep it up to date. I've only recently made the switch from WinXP to Ubuntu 7.10, in XP I just had to place the .ods file in the startupfolder, so every time I logged into WinXP the file opened up in OOCalc.

I've been searching these forums for the last few days, but to no avail.
Any help would be appreciated!

---

### Post by ajgreeny on 2008-01-16
What about the command in the session startup programs tab ```
ooffice -calc /path/to/file
``` I've never tried it or needed to but can't see why it wouldn't work.

---

### Post by no3 on 2008-01-16
That did the trick, thank you so much!

---

