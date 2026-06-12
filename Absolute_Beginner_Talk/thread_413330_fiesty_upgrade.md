---
title: "fiesty upgrade"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by abu-fatu on 2007-04-19
just finished the upgrade to fiesty. now i only have 800x600 resolution. any suggestions?

---

### Post by Tasu on 2007-04-19
Some more hints? Which is your Video adapter? intel? nvidia? ati? etc....

---

### Post by bikeboy on 2007-04-19
If you were using the nvidia driver previously, the kernel upgrade (part of moving to Feisty) may have interfered. You should try opening the Restricted Drivers Manager under System > Admin.

---

### Post by abu-fatu on 2007-04-19
nvidia glx-legacy

---

### Post by meborc on 2007-04-19
have you tried reconfiguring your X?
```
sudo dpkg-reconfigure xserver-xorg
```
chose the default answers, if you are not sure...
EDIT: i don't know about the legacy drivers, but the usual nvidia ones sometimes (dapper-> edgy) needed reinstalling after the kernel upgrade... don't know if the same applies to upgrading to feisty

---

### Post by abu-fatu on 2007-04-19
problem fixed removed nvidia driver  as bikeboy suggested thanks.

---

