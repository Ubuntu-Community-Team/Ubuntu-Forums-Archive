---
title: "Fresh Install, stuck at 640x480 Res"
date: 2005-09-24
forum: Absolute Beginner Talk
---

### Post by ZeroRelix on 2005-09-24
How would I fix? I can't change it no matter what I try.

---

### Post by papangul on 2005-09-24
What is your graphics chipset or graphics card? Also you may post the contents of /etc/X11/xorg.conf here.

---

### Post by ZeroRelix on 2005-09-24
One of those "Intel Extreme Graphics Controllers" My device manager says 82845G/GE Chipset.

---

### Post by papangul on 2005-09-24
BTW, you can always get hints regarding the problem by taking a look at
/var/log/Xorg.0.log, look for Errors (EE) and/or Warnings (WW)

---

### Post by bored2k on 2005-09-24
From a terminal try this:
```
sudo dpkg-reconfigure xserver-xorg
``` Then restart X (Ctrl+Alt+Backspace) or Reboot.

---

### Post by weasel fierce on 2005-09-24
Make sure, in the xorg.conf file, to have entered your monitors synch rates.

---

### Post by ZeroRelix on 2005-09-24
[QUOTE=weasel fierce]Make sure, in the xorg.conf file, to have entered your monitors synch rates.[/QUOTE]
 Figured it out guys, working with 1024x768 now(which is what i wanted). Thanks for all your help. ^_^

---

