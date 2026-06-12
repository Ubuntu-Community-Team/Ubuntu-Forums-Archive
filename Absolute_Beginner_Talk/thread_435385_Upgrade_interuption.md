---
title: "Upgrade interuption"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by jjasman5 on 2007-05-06
Help. 
I was upgrading Ububtu to 6.10, and was about an hour into the upgrade when I two back-to-back power flickers in about 4 seconds. Now when I boot/reboot the system I get the warnings about the interupted upgrades, the GNOME Desktop Manager comes up but I cannot enter my username (the box and buttons are greyed out).
Is there a way past the GNOME Desktop Manager, or a way to boot via a prompt to get back to the Ubuntu Desktop?

jjasman5

---

### Post by phidia on 2007-05-06
See if you can open CLI by pressing Alt+Ctrl+F1 together.  You have to start your internet from commandline and restart the upgrade. If you can't do that then perhaps you can use the "rescue a broken system" option on the live/install cd.

---

### Post by zvacet on 2007-05-07
**ctrl+alt+F1**


```
sudo aptitude update & sudo aptitude upgrade
```

---

