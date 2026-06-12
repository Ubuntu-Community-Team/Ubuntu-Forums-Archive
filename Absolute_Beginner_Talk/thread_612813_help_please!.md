---
title: "help please!"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by jerin on 2007-11-14
hii.i'm new to ubuntu.when i try to update i get a error message

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

what am i supposed to do??

---

### Post by Dr Small on 2007-11-14
> **jerin said:**
> hii.i'm new to ubuntu.when i try to update i get a error message

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

what am i supposed to do??
In the terminal (Applications > Accessories > Terminal)
Run:
```
sudo dpkg --configure-a
```

---

### Post by mikewhatever on 2007-11-14
> **jerin said:**
> hii.i'm new to ubuntu.when i try to update i get a error message

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

what am i supposed to do??

Go to Applications>Accessories>Terminal and type
> sudo dpkg --configure -a
enter your password and hit enter.

---

