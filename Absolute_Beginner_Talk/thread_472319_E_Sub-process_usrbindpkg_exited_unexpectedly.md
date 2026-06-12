---
title: "E: Sub-process /usr/bin/dpkg exited unexpectedly"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by notjohn101 on 2007-06-12
ok so ANYTHING dealing with dpkg returns this 

> E: Sub-process /usr/bin/dpkg exited unexpectedly  A package failed to install.  Trying to recover:

or

> Bus error (core dumped)

i googled it everyway i can any everyone says use "dpkg -configure -a" but all i get is that first error

u may be able to tell im a little frustrated....mainly cuz i cant fix it myself....but thanks in advance for the help

---

### Post by zvacet on 2007-06-12
```
sudo dpkg -configure -a
```

---

### Post by notjohn101 on 2007-06-13
all i get is > Bus error (core dumped)  after > sudo dpkg --configure -a

---

### Post by notjohn101 on 2007-06-13
bump

---

### Post by zvacet on 2007-06-14
[http://ubuntuforums.org/showthread.php?t=454759&highlight=segmentation]("http://ubuntuforums.org/showthread.php?t=454759&highlight=segmentation")

---

