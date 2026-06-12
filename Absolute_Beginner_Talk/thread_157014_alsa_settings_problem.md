---
title: "alsa settings problem"
date: 2006-04-08
forum: Absolute Beginner Talk
---

### Post by yohan on 2006-04-08
ive just installed a new kernel and installed the latest alsa drivers. Everything works good but when I try and change the settings with either alsamixer or gnome-alsamixer the settings arnt saved after reboot. Anyone know what this might be caused by?

Thank you!

---

### Post by hollywoodb on 2006-04-09
try
```
sudo alsactl store
```
to save your settings

---

