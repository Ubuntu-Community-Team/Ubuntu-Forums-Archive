---
title: "How to find detailed hardware information in linux?"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2008-01-30
Is there any way to find detailed hardware information when we are in linux?
for example VGA card model and brand, CPU detailed information...?
I find something in gnome-control-center but it is very limited and has no information about VGA.


Thanks

---

### Post by fatality_uk on 2008-01-30
Have you tried the menu System->Preferences->Hardware Information.
Gives you very detailed info for all hardware!

From a terminal
> hal-device-manager

---

### Post by Christmas on 2008-01-30
Info about your system is kept into a virtual directory /proc. Try commands like
```
cat /proc/cpuinfo
cat /proc/meminfo
```
There are probably GUI applications which take this info and show it to you into a more readable format, just search with APT.

---

### Post by oldos2er on 2008-01-30
lshw, lspci.

---

### Post by antisocialist on 2008-01-30
df -h

---

