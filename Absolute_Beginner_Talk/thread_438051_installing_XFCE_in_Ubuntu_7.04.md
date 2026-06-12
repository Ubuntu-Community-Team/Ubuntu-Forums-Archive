---
title: "installing XFCE in Ubuntu 7.04"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by linuxhippy on 2007-05-09
I did a search packages in synaptic and found quite a lot for XFCE.  I want to install the XFCE desktop in Ubuntu 7.04 along with all the accompanying goodies and other packages.  I'm thinking of this:

sudo apt-get install xfce*

Would this work?

---

### Post by Nythain on 2007-05-09
you should give a try to sudo apt-get install xubuntu-desktop
will install the xfce, and any apps that would be installed by downloading and installing the xubuntu (xfce version of ubuntu) disk

---

### Post by Kobalt on 2007-05-09
I'd recommend using ```
sudo aptitude install xubuntu-desktop
```In case you'd like to remove it afterwards it'll make things a bit cleaner.

---

### Post by Nythain on 2007-05-09
yeah... i use aptitude to install everything, but after reading that apt-gets autoremove is up to par with aptitude now a days, and the fact that most use apt-get in thier posts here, i didnt want to cause any confusion... but in this situation i guess i DEFINATELY should have suggested aptitude, given the large amounts of packages that are going to be associated with that metapackage

thanks

---

### Post by Kobalt on 2007-05-09
no prob :D

---

