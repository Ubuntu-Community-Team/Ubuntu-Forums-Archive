---
title: "another one of those xserver wont start problem"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by smurf killer on 2007-05-27
hi i know this has been asked 10000 times before but i haven't been able to find a solution. its the problem where it says "no screens found" i have tried to reconfigure it with dpkg-reconfigure xserver-xorg but i can't remember how i restart the xserver... i have tried to restart the computer after i made the reconfigure but with no result. anyone have some good advices? by the way this problem occured after using the build in updater to feisty

---

### Post by taurus on 2007-05-27
Boot into recovery mode from GRUB menu again and try to reconfigure X with

```
dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by smurf killer on 2007-05-27
tried the nv driver for my nvidia graphic card. but should i then boot in normal mode now?

---

### Post by taurus on 2007-05-27
Yes.  Reboot into normal mode.

```
shutdown -r now
```

---

