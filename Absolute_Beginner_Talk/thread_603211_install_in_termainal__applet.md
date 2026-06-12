---
title: "install in termainal  applet"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by ub9876 on 2007-11-04
what is the exact code for installing the wifi radar applet using the terminal/???

---

### Post by Hospadar on 2007-11-04
```
sudo apt-get install wifi-radar
```

And just so you know which parts are for what:
sudo - gives the command that follows root (admin) access
apt-get - this is the backend for the normal package manager, it handles all your packages
install - this is an argument for apt-get so it knows to install the packages, all the stuff after this are the packages you are installing

---

