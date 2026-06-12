---
title: "[SOLVED] ATI X1950 problem after enable restricted"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by doctorza on 2007-09-09
Hey LINUX users
I have a problem with my ATI X1950

When I enable restricted ATI drivers my startx give me a black screen.


any ideas how 2 fix this problem?
Thanks in advance

---

### Post by SOULRiDER on 2007-09-09
Try to reconfigure X and see what happens. Reboot to recovery mode and type:
```
sudo dpkg-reconfigure  xserver-xorg
```

---

### Post by doctorza on 2007-09-09
this work 2 restore my Ubuntu but now my Restricted ATI driver is again uncheck
How can I enable it with out getting the the black screen

---

### Post by andymushu on 2007-09-09
first, disable the drivers. then go to the add/remove programs and search for envy. download that, then run it (under system tools). click on the 3 button, download ati drivers. once it is all finished, restart your computer and if all goes well you should be able to login with the restricted drivers.

---

### Post by w4ett on 2007-09-09
Try following thhis sticky thread for installation of fglrx for ATI X-series cards:

[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

---

### Post by doctorza on 2007-09-09
donwload envy from there website 
[http://www.albertomilone.com](http://www.albertomilone.com)

and it works
THANKS andymushu

---

