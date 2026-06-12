---
title: "Package error message"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by captgadget on 2007-04-08
When I try to add a program I keep getting this error. 
E: /var/cache/apt/archives/libdbus-qt-1-1c2_0.62.git.20060814-1_i386.deb: files list file for package `hplip' contains empty filename

Does anyone know how to fix it? I've reloaded add/remove and synaptic with no luck.

---

### Post by taurus on 2007-04-08
Open a terminal and try

Applications -> Accessories -> Terminal
```
sudo aptitude clean
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by captgadget on 2007-04-08
Thanks but here is a screen shot of what I got,

---

### Post by woro2006 on 2007-04-21
SOLVED

rm /var/lib/dpkg/info/libdbus-qt*

---

