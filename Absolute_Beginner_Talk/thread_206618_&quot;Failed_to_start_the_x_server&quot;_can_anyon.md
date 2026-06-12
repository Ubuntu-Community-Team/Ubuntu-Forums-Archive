---
title: "&quot;Failed to start the x server&quot; can anyone help?"
date: 2006-06-30
forum: Absolute Beginner Talk
---

### Post by Rosanna on 2006-06-30
Someone has given me ubuntu burned onto a CD to install. It is ubuntu 6.06 LTS Dapper Drake.

I put it in the computer and told it to boot from the CD, I selected English and the start/install option. It seemed to be installing fine until I got this message:

Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?
<Yes>s>   <No>o>

...so I clicked yes

X window system version 7.0.0
Release Date : 21 December 2005
X protocol version 11, Revision 0, Release 7.0
Build operating system: linux 2.6.12 i686
Current Operating System: linux ubuntu 2.6.15-23-386 #1 PREEMPT Tue
May 23 13:49:40 UTC 2006 i686
Build Date: 16 March 2006
Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting, (++) from command line, (!!) notice, (II) informational, (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Jun 30 16:24:42 2006
(==) Using config file: "/etc/X11/xorg.conf"

<Ok>

Would you like to view the detailed X server output as well?
<Yes>    <No>

... got the same message as above

The server is now disabled. Restart GDM when it is configured correctly.

<Ok>

And then I didn't know where to go from there. Can anyone help? Thankyou in advance.

---

### Post by jrattner on 2006-06-30
Is during the Install or post-install?

If its post-install run the following command and paste the output in this thread:
```
cat /var/log/Xorg.0.log
```

This will be need in order to diagnose the situation more easily.

---

### Post by Rosanna on 2006-06-30
It comes up when I try to install it.

---

### Post by nanotube on 2006-06-30
after it says "xserver now disabled..." run command
dpkg-reconfigure xserver-xorg
and when you are choosing the video driver, choose "vesa"
that would have a good chance of making a working xserver.

btw, what video card are you using...? and, does running from the livecd (without install) work?

---

### Post by Rosanna on 2006-06-30
Thankyou very much nanotube I will try that. 

I'm sorry but I don't have a clue what video card I'm using. How would I run it from the live CD? All I did was put the CD in, turn the computer on, press F12 to view the boot menu and select boot from CD, then I clicked on Install/Load (or was it run?) ubuntu.

---

### Post by FUSION6 on 2006-07-03
thanks nanotube that fixed my problem

---

