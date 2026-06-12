---
title: "SIOCGIFFLAGS error: No such device"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by Rockyhead on 2006-07-18
Hi!

I just finished installing Ubuntu 6.06 Desktop AMD64-version on my Fujitsu-Siemens Amilo A1650G - laptop. I made it a dual-boot system with WinXP. The problem is, that now the net won't work.

Everything worked fine when I ran Ubuntu from the CD, and I can also connect when I boot to Windows -> the connection and devices work, suggesting a problem with Ubuntu.

The network connection logo at the upper right corner of the screen suggests at some kind of an error, and when I click on it, a window pops up saying: "SIOCGIFFLAGS error: No such device"

What could be the problem?

Thanks in advance :D

---

### Post by John.Michael.Kane on 2006-07-18
Right click the (Network Monitor),and manualy type in eth0 in the box. also a bug report has been filed [**[COLOR="Blue"]gnome-netstatus-applet does not show eth0[/COLOR]**]("https://launchpad.net/distros/ubuntu/+source/gnome-netstatus/+bug/21234")

---

### Post by Rockyhead on 2006-07-19
Hey thanks man, that really saved my day! :KS

---

### Post by marytgras on 2006-08-12
Thanks as well, this one helped me out alot!

---

