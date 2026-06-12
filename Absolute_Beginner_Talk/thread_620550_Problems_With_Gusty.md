---
title: "Problems With Gusty"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by nik62790 on 2007-11-22
Gusty was working just fine for about a week and then this last time when i went to use it instead of loading a graphical login there was a black screen with plain white that said *******-laptop login:. then after i  typed in my user name and password it went and displayed me the line as if i were in the terminal. so when i typed in a command to start a program it told me that the X server had a fatal error and could not be started.  if someone could help me that would be very much appreciated.  thank you.

---

### Post by taurus on 2007-11-22
Reconfigure your X server again with

```
sudo dpkg-reconfigure xserver-xorg
startx
```

---

### Post by nik62790 on 2007-11-22
THANK YOU!!!!  everything is working just fine now.  thank you again.

---

