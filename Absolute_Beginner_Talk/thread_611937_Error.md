---
title: "Error"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by AgHawke on 2007-11-13
Hi All:

 I was trying to install programs in synaptic program manager and it locked up.This is the error code i got   dpkg interrupted manually run E:'dpkg  --configure -a' to correct
E:cache>open()failed,please report.Now I tried to run this code into the terminal with no luck my question is will I have to reinstall Ubuntu? thanks

AgHawke

---

### Post by taurus on 2007-11-13
Close synaptic.  Then, open a terminal and run

```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```
If there is an error message, post it here.

---

### Post by WebSiteGuru on 2007-11-13
He have not left, just changed name at login.

---

### Post by Tux.Ice on 2007-11-13
im sorry i cant help you try doing a reinstall??

---

### Post by AgHawke on 2007-11-13
Hi All:

 Big thanks to you Taurus your code worked!!!!

AgHawke

---

