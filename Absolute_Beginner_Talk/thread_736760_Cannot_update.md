---
title: "Cannot update"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by OlyPerson on 2008-03-26
Recently, I have not been able to install update because of a message I get in the update manager that looks like:
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```
What can I do to fix this?  I think it started happening when the update for something with bzip came along for an update.
Thanks.

---

### Post by SunnyRabbiera on 2008-03-26
yeh easily fixed, just do as it suggests and open a terminal and put in dpkg --configure -a
it should fix it, this stuff happens sometimes.

---

### Post by wormser on 2008-03-26
Applications> Accessories> Terminal

```
sudo dpkg --configure -a
```

---

