---
title: "Install Interuption with Sun Java 5"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by clunky on 2007-09-01
I am new to Ubuntu and have had a problem during an install of Sun Java 5, programs where installing fine however ceased after power interruption.  Any time I try to re-install sun-java 5 or any other program for that matter I get the following message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I am not sure what I have to do or change to allow me to re-install or uninstall Java altogether

Any help kindly appreciated

---

### Post by wormser on 2007-09-01
Applications> Accessories> Terminal

```
sudo dpkg --configure -a
```

---

### Post by clunky on 2007-09-01
thanks, that worked.....

Cheers

---

