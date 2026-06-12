---
title: "installed Ubuntu but get error at loading"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by fiver22 on 2006-07-26
I just finnished installing ubuntu 6.06 using the 'alternate' cd as I was getting an error using the regular CD -while ubuntu is now loaded onto my pc and I can dual boot I now have another problem: ubuntu starts to load and then I get this error:
"Failed to start the X server (your graphical interface). It is likely that it is not set up correctly would you like to view the X server output to diagnose the problem?"
Selecting YES to diagnose the problem gives me: 
"x window System Version 7.0.0
Release Date 21 December 2005
XProtocol Version 11, Revision 0, Release 7.0
Build Operating System: Linux 2.6.12 i686
Current Operating System: Linux ubuntu 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686
Build Date: 16 March 2006
Before reporting problems, check [http://wiki.x.org](http://wiki.x.org) to make sure you have the latest version.
Module Loader present
Markers: (--probed, (**)from config file, (==)default setting, (WW)warning, (EE)error, (NI)not implemented, (??)unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Jul 25 17:10:22 2006
(==)Using config file: "/etc/X11/xorg.conf"
--I hit OK and it says: 
"The X server is now disabled. Restart GDM when it is configured correctly".
It then brings me to what I think is the command line (I can type there, at least).
Does this have anything to do with the fact I'm using an ATI X800 PCIe gfx card? -can anyone suggest a way I can get this working?
[I posted earlier with very similar problem (using the Live CD and not being able to install) and got some very helpful answers -I hope this new problem warranted a new thread]
Thanks again for any help/suggestions.

---

### Post by gingermark on 2006-07-26
I have no experience with ATI cards, but do ```
sudo dpkg-reconfigure xserver-xorg
``` to reconfigure X.

You might want to try using the VESA driver - this will normally at least allow you to start X and get into GNOME. From there you will then want to [enable the extra repositories](https://help.ubuntu.com/community/Repositories/Ubuntu), and then you should be able to [install the official drivers](http://ubuntuforums.org/showthread.php?t=75378).

Good luck.

---

### Post by fiver22 on 2006-07-26
Thanks very much, gingermark -it's working now

> **gingermark said:**
> I have no experience with ATI cards, but do ```
sudo dpkg-reconfigure xserver-xorg
``` to reconfigure X.

You might want to try using the VESA driver - this will normally at least allow you to start X and get into GNOME. From there you will then want to [enable the extra repositories](https://help.ubuntu.com/community/Repositories/Ubuntu), and then you should be able to [install the official drivers](http://ubuntuforums.org/showthread.php?t=75378).

Good luck.

---

