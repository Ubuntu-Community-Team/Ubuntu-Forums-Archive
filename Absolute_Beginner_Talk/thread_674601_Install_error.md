---
title: "Install error"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by KyleVeg on 2008-01-21
Every time I try to update or install, I get this error. Then when I try to run the dpkg configure thing it tells me I need superuser privilege. I have no clue what to do. Help please!

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by overdrank on 2008-01-21
> **KyleVeg said:**
> Every time I try to update or install, I get this error. Then when I try to run the dpkg configure thing it tells me I need superuser privilege. I have no clue what to do. Help please!

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

HI and welcome then you must run the command ```
sudo dpkg --configure -a
```
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

