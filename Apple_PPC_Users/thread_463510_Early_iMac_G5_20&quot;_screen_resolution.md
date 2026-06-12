---
title: "Early iMac G5 20&quot; screen resolution"
date: 2007-06-03
forum: Apple PPC Users
---

### Post by zapcojake on 2007-06-03
Hello, I have an early (no iSight) 20" G5 iMac with nVidia graphics.  I can't seem to get the screen resolution better than 1024x768.  Is this normal?  Is there a fix?  Thanks --Jake

---

### Post by luckyd on 2007-06-03
> sudo dpkg-reconfigure xserver-xorg Run that in the terminal. Then keep everything at the defaults except for the dialog that shows resolutions. Once there star only the resolutions that you want and unstar the others. Reboot, and you should be good  ;)

---

### Post by stmiller on 2007-06-03
You may have to edit the xorg.conf file like this from a terminal:

sudo gedit /etc/X11/xorg.conf

and find the line that says

Driver  "fbdev"

and change it to

Driver "nv"

if it's not already like that.

---

