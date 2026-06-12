---
title: "green lines on buttons"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by captainroin on 2006-09-21
the buttons on pop up windows (i.e. 'this document has changed save?') have green lines on them and just dont look right till i mouse over them, then they look fine. sometimes when i mouse off they go back to looking funny, sometimes not. i'd do a screenshot but i'm at work.

anyone else ever see this?

P4M 1.7Ghz
512MB RAM
some sort of ATI radeon mobile vid card (its a laptop)
Ubuntu 6.06
i686 kernel

thanks for any help.

---

### Post by petri on 2006-09-21
You need to install ati drivers. Probably fglrx-drivers, try first with 

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

---

### Post by captainroin on 2006-09-23
ok... that seems pretty straight forward. but i already have the newest installed?? can i just un-install this one and reinstall the new one? i'm pretty new to this command line stuff as well.

```
ryan@wallace:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

ryan@wallace:~$ sudo apt-get install xorg-driver-fglrx
Reading package lists... Done
Building dependency tree... Done
xorg-driver-fglrx is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.

```

---

### Post by petri on 2006-09-23
I seems like sudo apt-get install xorg-driver-fglrx doesn't give you 3D. You are still on mesa drivers (OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org))

Use method 2 on [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide) then you don't have to worry about uninstalling.

CLI is pretty easy when you follow a HOWTO. You just highlight the text with your left mousebutton and paste it with clicking your scrollwheel in terminal, and press Enter.


EDIT:
P.S. Do run this command first at terminal ```
lspci
``` and look for which ATI you have. It should be better than Radeon 9500 but not better than the X-series cards up to X1900 according Method 2. But my AIW 8500 does work.

---

### Post by rölli on 2006-09-29
I had have the same problem and found out more about this problem already some time ago here in the forums (don't remember where). You are probably using the open source radeon driver. If you cannot install the closed source driver from ATI because your card is too old and no longer supported, you can add the line

Option   "RenderAccel"   "off"

to your /etc/X11/xorg.conf config file (Device Section). This should do the job after restarting the X-server.

Regards, Rölli

---

