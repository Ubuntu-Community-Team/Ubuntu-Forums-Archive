---
title: "Ubuntu won't install on LCD monitor"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by jtx472 on 2007-03-14
I installed Ubuntu on one computer with a CRT monitor no problem.  I really like Ubuntu and would like to dispense with Windows XP altogether.  The problem is my main computer has a LCD monitor and Ubuntu will not install.  Here's what I get:

Failed to start the X server (your graphical interface).  It is likely that it is not set up correctly.  Would you like to view the X server output to diagnose the problem?
                                                                  YES
X Window system version 7.1.1
Release date:  12 May 2006
X Protocol version 11, Revision 0, Release 7.1.1
Build operating system:  Linux 2.6.15.7 i686
Current operating system:  Linux Ubuntu 2.6.17-10-generic #2 SMP Fri
Oct 13  18:45:35 UTC 2006 i686
Build date:  07 July 2006
Before reporting problems, check [http://wiki.x.org](http://wiki.x.org) to make sure you have the latest version.
Module loader present
Markers: (--) probed, (**) from config file, (==) default setting
(**) from command line, (!!) notice, (II) informational
(WW) warning, (EE) error, (NI) not implemented, (??) unknown
(==) Log file:  "/var/log/Xorg.0.log"
Time Wed Mar 14  11:22:38 2007
(==) Using config file: "/etc/X11/xorg.conf"

Which is all Greek to me.  Any assistance would be greatly appreciated.

---

### Post by bulldog on 2007-03-14
You have to reconfigure xserver with the next command,
```
sudo dpkg-reconfigure xserver-xorg
```
Choose the right resolution for your LCD screen.

Maybe it's better to install drivers for your graphics first.

---

### Post by Songwind on 2007-03-14
You could use the alternate install CD and use the text-based installer.

There is also an option at the bottom of the first screen (where you choose "start or install Ubuntu") where you can change graphics options.  See if you can set it to something more closely resembling your hardware, or a vanilla "vga" option.

Good luck!

---

