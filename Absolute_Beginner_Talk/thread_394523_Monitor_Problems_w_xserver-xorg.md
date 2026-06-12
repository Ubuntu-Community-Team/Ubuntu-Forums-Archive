---
title: "Monitor Problems w/ xserver-xorg"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by Spicy McHaggis on 2007-03-27
my monitor settings didn't recognized by the xserver when i booted up after install. Did the recongifure of xserver-xorg when in safe mode, inputted my monitor's specs in advance mode selected 24-bit colour and got this message:

xserver.xorg.postinist warning: overwriting possibly customized configuration file; backup in /etc/x11/xorg.conf.200703262240

What is this? Confuzzled as all get out - could someone please help????????

BTW, monitor is BenQ FP222W rez 1680x1520

Thanks a bunch whoever answers


):P
Spicy

---

### Post by nickoli_02 on 2007-03-27
What it means is that your xorg.conf (the configuration file for xserver) is being overwritten with what you just specified using dpgk-reconfigure. It's perfectly fine, and it even creates a backup of your previous settings with the timestamp appended!

---

### Post by Spicy McHaggis on 2007-03-27
but i rebooted and the login screen is still corrupted - now what?

Spicy

---

