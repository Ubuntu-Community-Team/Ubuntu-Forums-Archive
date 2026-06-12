---
title: "add\remove not downloading packages!"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by exneo002 on 2008-02-27
I am using add\remove and whenever I try to install a package I select and hit apply then it goes but it wont find the package or download help!

---

### Post by taurus on 2008-02-27
Do you have all the repos enable in /etc/apt/sources.list?  

```
cat /etc/apt/sources.list
```

---

### Post by LunatikOwl on 2008-02-27
Do you know the name of the package?
Try removing it in apt-get/aptitude/synaptic

---

### Post by Iehova on 2008-02-27
Go to System > Administration > Software sources; check everything under "Downloadable from the internet" and uncheck the CD if it is checked. Now try again.

---

### Post by exneo002 on 2008-02-27
oh my network proxy settings were screwed up

---

