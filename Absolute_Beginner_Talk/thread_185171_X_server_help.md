---
title: "X server help"
date: 2006-05-31
forum: Absolute Beginner Talk
---

### Post by jerseybear on 2006-05-31
I'm a complete newbie to linux and ubuntu and need some help with my instalation.  

When I boot into ubuntu, it is telling me that I'm having problems with my X server and taking me to the command line prompt.  At this point, I'm not sure what to do.

Incidentally, during start up, the screen goes from GUI to command line during clock sync -- which fails.  This seems unrelated, but who knows.  

Also, I'm running this on a amd athilon 64 x2 machine in dual boot mode.  Does ubuntu work on the x2?

Finally, my ultimate goal is to set up a forum using linux-apache-php bb-mysql.  Considering I'm new to linux and already having problems -- should I use the windows os?  I have to learn the other software packages as well.

Thank you very much.

---

### Post by bruce89 on 2006-05-31
```
sudo dpkg-reconfigure xserver-xorg
``` should fix the X server issues.
Anyway, welcome!

---

### Post by tseliot on 2006-05-31
[QUOTE=bruce89]```
sudo dpkg-reconfigure xserver-xorg
``` should fix the X server issues.
Anyway, welcome![/QUOTE]
That's right, and remember to select the "vesa" driver

---

### Post by MTK on 2006-05-31
I've encountered a similar problem, but I have not performed a full installation, I'm using the 'live CD'.  Specifically, I get a box on my screen with an error message similar to "Error starting X windows - do you want to see the details?"  There are "Yes" and "No" boxes to select, but before I can get to them, the startup continues.  Eventually, I get to a command line.

Will this same command work in my situation? With a 'live' CD?

---

### Post by bruce89 on 2006-05-31
[QUOTE=MTK]Will this same command work in my situation? With a 'live' CD?[/QUOTE]
Yes, but you will have to run this command:
```
sudo gdm
```

---

### Post by jerseybear on 2006-05-31
Wow -- thank you so much for your quick replys.  I will try this tonight.

---

