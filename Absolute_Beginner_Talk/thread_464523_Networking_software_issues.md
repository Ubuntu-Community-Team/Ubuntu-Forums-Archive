---
title: "Networking software issues"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by doctorproteus on 2007-06-04
I am running Edgy on my laptop and lost my wireless connection to the internet.  I tried to set it up again with System - administration - networking, but when I enter my password, I get a bug buddy report.  I would love to share it all but it would take about three hours to type and I have no connection with that computer.  Any help?

---

### Post by scrooge_74 on 2007-06-04
try changing things in /etc/network/interfaces

and comment out your wireless connection so it detects it again

change it to 

auto eth1
iface eth1 inet dhcp

(replace eth1) with the name of your wireless card

also check that you have network manager working and that the applet is running on one of your desktop bars if not from a terminal type nm-applet

also what wireless card you have some are more tricky than others.

---

