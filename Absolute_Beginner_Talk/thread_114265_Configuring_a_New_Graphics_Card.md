---
title: "Configuring a New Graphics Card"
date: 2006-01-08
forum: Absolute Beginner Talk
---

### Post by bjp on 2006-01-08
Hi, I wonder if anybody could help me. I've just changed my graphics card from an ATI Radeon to an Nvidia Geforce card. When I boot Ubuntu I get an error message saying my card is not configured and the GUI cannot start, so I can only boot to the prompt. Is it easy to do without reinstalling ubuntu from scratch.

---

### Post by jon_z on 2006-01-08
[http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074)

I hope that helps..
If you have already installed the drivers try doing a:

$  sudo dpkg-reconfigure xserver-xorg  

and when the driver section comes up use nvidia instead of fglrx

---

### Post by poofyhairguy on 2006-01-08
[QUOTE=jon_z][http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074)

I hope that helps..[/QUOTE]

There is an easier way to install the Nvidia drivers:

[http://help.ubuntu.com/starterguide/C/faqguide-all.html#installnvidiadriver](http://help.ubuntu.com/starterguide/C/faqguide-all.html#installnvidiadriver)

---

