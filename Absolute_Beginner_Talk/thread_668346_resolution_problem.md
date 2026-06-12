---
title: "resolution problem"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by SpinningAround on 2008-01-15
Got a small problem with resolution, I can only get 1600x1400 even if I try to change it in nvidia-settings or the screen resolution settings under settings does nothing happen, it's simply at 1600x1400 and impossible to change.

edit: the problem is on a other computer then the one in my sign.

---

### Post by OffAxis on 2008-01-15
you can try doing a
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
or a
```
sudo xrandr --fb 1024x768
```
to set the resolution immediately to 1024x768


dpkg-reconfigure = reconfigure an existing package
-phigh = only high priority options on the specified package (xserver-xorg)

You should look up your monitor's specs and you can use that dpkg-reconfigure command to add in the name of the monitor and exactly what the resolutions should be, refresh rate, etc.

You can also try this doc:
[https://help.ubuntu.com/community/FixVideoResolutionHowto]("https://help.ubuntu.com/community/FixVideoResolutionHowto")

---

