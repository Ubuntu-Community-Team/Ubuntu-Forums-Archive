---
title: "[SOLVED] Nvidia geforce ti 4200 wont enable desktop effects"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by moonfriedpotatoes on 2008-01-29
i've tried so many things to get my nvidia driver configured correctly.  installing the newest kernel, installing from nvidia site, installing using envy, reconfiguring xorg following the many procedures here (changing nv to nvidia for example), sudo nvidia-glx enable, pretty much everything i could find.  half the time i enable the restricted driver my resolution is greatly reduced, after which  i have to edit xorg by adding in the resolution mode lines, and even then the reconfig falls down after i reboot and STILL desktop effects wont enable.  i reinstalled ubuntu from cd and started afresh, and have managed to get the nvidia legacy driver installed and fixed the resolution issue, butt he effects still wont enable.  im pissed.  i really want the fancy cube desktop dealio.  the restricted device manager says the driver is in use and enable.  grrr

---

### Post by moonfriedpotatoes on 2008-01-29
commented out the amount of memory necessary to enable the driver in /usr/bin/compiz  as per  [http://ubuntuforums.org/showthread.php?t=582818](http://ubuntuforums.org/showthread.php?t=582818).  thanx

---

