---
title: "problem with graphics"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by boxercbuk on 2007-04-29
Im ruinning pc I386 ubuntu 7.04
Within the desktop the restricted drivers installed the wrong graphics drivers and I would like to reset to the restricted drivers but I can now only access the command prompt is there a code to reset the drivers back to restricted so i can access the desktop.
any help appreciated 
cheers

---

### Post by Obor on 2007-04-29
This should help
```
 sudo dpkg-reconfigure xserver-xorg
```
leave default answers except for the one about your driver, choose the driver you want

---

### Post by boxercbuk on 2007-04-29
thanks will try now

---

### Post by boxercbuk on 2007-04-29
thanks back in desktop and now set up perfectly no longer using restricted drivers cheers:KS :KS :KS :KS :KS :KS :KS

---

