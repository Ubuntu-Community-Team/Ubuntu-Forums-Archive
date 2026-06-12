---
title: "Failed to start X server"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by fiver22 on 2006-07-25
I'm booting from the CD (ubuntu 6.06LTS) and get to a screen that asks me to "Start or install Ubuntu" -I select that and it starts configuring drivers, etc for a minute.
Then the screen goes blank for a sec and this message comes up: "Failed to start the X server (your graphical interface). It is likely that it is not set up correctly would you like to view the X server output to diagnose the problem?"
Selecting yes gives me this: x window System Version 7.0.0
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
--I hit OK and it says "The X server is now disabled. Restart GDM when it is configured correctly".
I then hit OK and it brings me to a command prompt (I think that's what it is) that will let me type but no commands seem to work.

Any ideas what my next step should be? -sorry for the long (and maybe unnecessary) quotes but I'm completely new to this and not sure which info is relevant.
Thanks again for any help.

---

### Post by taurus on 2006-07-25
What video card do you have because it is the problem for the desktop (LiveCD) version?  Therefore, use the alternate CD to install it since it's a text base (like the old way) installer...

---

### Post by fiver22 on 2006-07-25
I have an ATI Radeon X800 -I'm downloading the alternate CD like you suggested but I'm worried that it'll be much harder for me than the graphical install -any hints/suggestions would be appreciated.


> **taurus said:**
> What video card do you have because it is the problem for the desktop (LiveCD) version?  Therefore, use the alternate CD to install it since it's a text base (like the old way) installer...

---

### Post by taurus on 2006-07-25
It is not any harder than the LiveCD.  In fact, if you install the previous version, Breezy, that was how you would install it...  The new GUI installer from LiveCD is new in Dapper.

---

### Post by fiver22 on 2006-07-26
So assuming the alternate works and I install it correctly do you think I'll have any problems seeing I'm using an ATI X800 as a video card?
-Thanks again for your time, and suggestions.

> **taurus said:**
> It is not any harder than the LiveCD.  In fact, if you install the previous version, Breezy, that was how you would install it...  The new GUI installer from LiveCD is new in Dapper.

---

### Post by nathandh on 2006-07-26
> **fiver22 said:**
> So assuming the alternate works and I install it correctly do you think I'll have any problems seeing I'm using an ATI X800 as a video card?
-Thanks again for your time, and suggestions.
I have a similar gpu (namely the X850) and I've encounterd the same problems when installing from the LiveCd but the alternate installer worked fine and I'm runing Ubuntu without any problems now and didn't come across any x server problems anymore.

---

