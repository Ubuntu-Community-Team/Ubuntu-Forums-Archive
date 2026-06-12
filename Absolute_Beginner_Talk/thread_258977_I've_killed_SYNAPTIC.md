---
title: "I've killed SYNAPTIC"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by dmpo5450 on 2006-09-16
E: Type 'file:///home/dmpo5450/Desktop/eek-0025c091b3.desktop' is not known on line 23 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

This is the error I get when I open it.  How do I fix?  Thanks.

---

### Post by jordanmthomas on 2006-09-16
Press Alt + F2
type
```
gksudo gedit /etc/apt/sources.list
```
Go to line 23 and remove it, as it certainly does not belong there.
Then:
```
sudo apt-get update
```
and try to launch synaptic

---

### Post by dmpo5450 on 2006-09-16
Thanks a million.  That seems to have fixed it.  Still trying to figger out how I did it.  Learn something new about Ubuntu everyday.  Thanks again for the quick response.:D

---

### Post by jordanmthomas on 2006-09-16
Good luck on figuring out how you did it...I sure don't know what you did  :)

---

