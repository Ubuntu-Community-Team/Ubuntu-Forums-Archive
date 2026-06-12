---
title: "AMD64 issues"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by clifford on 2006-11-19
I am brand new at this linux thing and I need some help with installing programs....I am trying to use wine and update my video card..ATI Radeon 1100 and it says I need xfree86......

---

### Post by hollaburoo on 2006-11-19
Wait, are yout trying to use wine to install video card drivers?  If so, I'm afraid that won't work.  But you should be able to install drivers for your card by typing ```
sudo apt-get install linux-restricted-modules-'uname -r' xorg-driver-fglrx
``` in a console.  As for wine, what programs do you want to install?

---

