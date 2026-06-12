---
title: "hmm another install/update problem?"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by djmaxmalta on 2008-03-19
well yes i got this message after i re-installed kubuntu and ubuntu on 2 seperate hdds and ubuntu was showing this before i installed kubuntu on my slave hdd

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


well how do i fix this?

---

### Post by jan quark on 2008-03-19
as a start run
```
sudo dpkg --configure -a
```
in terminal



> Edit: The quark moves at light speed.
edit: never say it that way /quark 
but you are right :)

---

### Post by glennric on 2008-03-19
Do what it says + sudo.  Type
```
sudo dpkg --configure -a
```
in a terminal.

Edit:  The quark moves at light speed.

---

