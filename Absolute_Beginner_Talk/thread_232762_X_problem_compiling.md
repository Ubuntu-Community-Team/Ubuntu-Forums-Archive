---
title: "X problem compiling"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by qazwsx on 2006-08-09
So I have build-essential installed but I get almoust everytime this message when I try to compile:

checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!

Seemed to work for anyone but me. What Ia m missing?

Sorry if someone answered on similar thread. I just didn't find similar thread

---

### Post by mlind on 2006-08-09
What are you compiling exactly? You probably need to install **xserver-xorg-dev** or similar build dependency.

---

### Post by tseliot on 2006-08-09
```
sudo apt-get build-dep xserver-xorg
```

if you need the dependencies to build the xserver

---

### Post by qazwsx on 2006-08-10
Thanks a lot

---

