---
title: "gparted not present after install"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by lastelement0 on 2007-08-26
i have an external drive i am trying to partition using gparted. however my issue does not come from actually partitioning as i can't even locate gparted after install i ran ```
sudo apt-get install gparted
``` followed by ```
./Gparted
``` once it finished installing the package. however nothing is visible in my system tool menus or with the other program executables.

what to do?

---

### Post by Hobo Joe on 2007-08-26
Use the live CD for any partitioning, you can't partition while the drive(s) are mounted.

---

### Post by Dr Small on 2007-08-26
Try:
```
gksudo gparted
```

Or go to System > Administration > Gnome Partion Editor

---

