---
title: "Black screen after upgrading"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by Fady Effat on 2007-10-22
Hey Everyone , i have a problem with my Gutsy ubuntu , after upgrading to 7.10 from 7.4 compiz didn't work at first it said xgl not present so i had to install a package then my borders disappeared so i googled and found out i had to add lines to xorg.conf after doing and rebooting my screen went black and i can't do anything except from recovery mode , anyone can help 

Dell 6400
Ati x1400
Core 2 Duo 2 Ghz
1 GB Ram
120 HDD
Gutsy

---

### Post by sugarland2k on 2007-10-22
To reconfigure your X-Server

back it up first!
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

sudo dpkg-reconfigure xserver-xorg

This is a script to configure the xserver.  Mostly you can accept the defaults, unless you are aware of a keyboard or mouse requirement that is different than the default.  When you get to the display driver, choose "VESA" rather than the one for your graphics card.  When you get to the monitor, make sure to "x" the resolution that you want for your desktop.  Set the refresh range as appropriate for your monitor.  Finish the script, then type in "startx" and you should get a graphical desktop.

Check out [http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox) 
a most excellent website for help...

Good luck, let us know how it turns out.

---

### Post by Fady Effat on 2007-11-07
thanks man that really done it

---

