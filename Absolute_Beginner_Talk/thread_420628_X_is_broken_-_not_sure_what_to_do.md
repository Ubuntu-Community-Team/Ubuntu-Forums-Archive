---
title: "X is broken - not sure what to do"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by OMRebel on 2007-04-23
I'm having a problem.  The X Server won't start up.  I'm running Fiesty.  I had disabled the restricted video driver, and restarted X, and now I'm getting the following error:

"Failed to start X server (your graphical interface).  It is likely that it is not set up correctly.  Would you like to view the X server output to diagnose the problem?"

When I say Yes, I get the following information:

"X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux brad-ubuntu 2.6.20-15 generic #2 SMP
Sun Apr 15 07:36:31 UTC 2007 i686
Build Date: 04 April 2007
Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
(++) from command line, (!!) notice, (II) informational,
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Apr 23 19:25:53 2007
(==) Using config file: "/etc/X11/xorg.conf"
(EE) Failed to load module "fglrx" (module does not exist, 0)
(EE) No drivers available.

Fatal server error:
no screens found"

Please help.  I promise not to screw it up again. lol

---

### Post by Najand on 2007-04-23
In terminal type:
```

sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r) #Okay if it is already installed
sudo apt-get install xorg-driver-fglrx
sudo depmod -a

```
See if it works or not. If not, I have another clue for that. Just inform me the result.

---

### Post by markl187ld on 2007-04-23
Log in to the terminal and type:

```
sudo nano /etc/X11/xorg.conf
```

Scroll down to Section "device" and change "fglrx" to "ati"

Ctrl + X to exit and "Y" to save the file

Reboot. 

Once you're back into X, reinstall the fglrx module and edit the xorg.conf back to read "fglrx" instead of "ati" and then reboot.

---

### Post by Zzl1xndd on 2007-04-23
If you the disabled your  video driver that would be the problem. Using "sudo dpkg-reconfigure xserver-xorg" (without the quotes) and answering the questions should get you back up.

---

### Post by OMRebel on 2007-04-23
Thanks guys.  I went with tweaked's recommendation, and that got it working.

---

