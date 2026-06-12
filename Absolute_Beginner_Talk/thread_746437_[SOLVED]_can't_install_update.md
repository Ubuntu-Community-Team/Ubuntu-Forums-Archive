---
title: "[SOLVED] can't install update"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by Joseph5000 on 2008-04-05
I get this error message and have no clue what to do with it. Any help is appreciated

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by SunnyRabbiera on 2008-04-05
this is a common error, no worries.
just open up a terminal and do as it said, just type or copy this in the terminal: sudo dpkg --configure -a

---

### Post by Joseph5000 on 2008-04-05
Hi Sunny, Thanks I did as you did and my computer did something, but what did it do? Did it install the updates??

---

### Post by bumanie on 2008-04-05
That error occurs usually as the result of some interuption to the download that was occuring and the package is only partially downloaded.
> sudo dpkg --configure -a  allows the package to resume downloading from the spot it was up to.

---

