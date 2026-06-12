---
title: "Ubuntu Resolution Problem"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by Dr Maximus on 2007-01-30
When I install Ubuntu to a PC. I get the resolution set to the highest possible automaticly. When I reset the 17" resolution to 1024x768 it reboots and again the resolution has not changed. The icons are so small it effect my eyes. I want to use it but cant get the resolution set lower

Please help
Rod

---

### Post by taurus on 2007-01-30
Open a terminal, Applications -> Accessories -> Terminal, and remove the resolutions you don't want to use in /etc/X11/xorg.conf.

```
gksudo gedit /etc/X11/xorg.conf
```
Otherwise, reconfigure X again with

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

