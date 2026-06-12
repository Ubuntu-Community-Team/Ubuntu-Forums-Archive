---
title: "Resolution Problems"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by klickzone on 2006-08-14
Ok, so I got ubuntu yesterday (my first linux disrto as well!), and am mostly enjoying so far.  I have had two problems with it.  The first was setting up the drivers for my broadcom wireless card, which I have now solved (thanks to the excellent wiki :D ), but the other still remains.

My screen resolution is impossible to change from anything higher than 640x480, which is extremely small, seeing as this moniter is designed for a natural resolution of 1280x1024 (LCD).  I am running on an ati X200 integrated graphics chipset, and even after downloading and installing the ati drivers (flrx), the resolution still fails to switch to anything higher using the screen resolution changer under System>Preferences>Screen Resolution.

Any help?

---

### Post by davebgimp on 2006-08-14
You probably need to manually edit your xorg.conf file.
Here's a howto guide on managing that:

[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)

Check the part called "Getting the Right Mode for an LCD monitor"

---

### Post by bruce89 on 2006-08-14
You can also do this in the terminal:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

