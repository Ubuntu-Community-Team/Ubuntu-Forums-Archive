---
title: "Can't Update/Error Message (E: dpkg was interrupted)"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by fetzkom on 2007-10-22
I am running 7.04, 64 bit version. I can't get into the package manager to install anything, let alone try to upgrade to 7.10. This is the error message I get continually:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

E: _cache->open() failed, please report.

What do I do?

---

### Post by overdrank on 2007-10-22
> **fetzkom said:**
> I am running 7.04, 64 bit version. I can't get into the package manager to install anything, let alone try to upgrade to 7.10. This is the error message I get continually:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

E: _cache->open() failed, please report.

What do I do?

HI and welcome, you just runt that command in the terminal 
```
sudo dpkg --configure -a
``` the terminal is located under applications, accessories.

---

