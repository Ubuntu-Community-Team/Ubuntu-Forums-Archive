---
title: "Need help setting up graphics card"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by Feba on 2007-04-03
Well I had been using an ATi Radeon 9550 graphics card when I installed yesterday, which for whatever reason ubuntu wouldn't let go over 1024x768 and would apparently not use for games. I decided to try my old MX440 GeForce, however upon starting up, Xwindows wouldn't open. I've followed some guides to install nvidia drivers, and they seem to be working, however when I attempt to startx I get an error saying 

Build Operating System: Linux 2.6.15.6 i686
Current Operating System: Linux <PC name> 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686
Built Date: 07 July 2006
    Before Reporting Problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version
Module Loader Present
Markers: (--) probed, (**) from config file, (==) default setting,
            (++) from command line, (!!) notice, (II) informational,
            (WW) warning, (EE) error, (NI) not Implemented, (??) unknown.
(==) Log File: "var/log/Xorg.0.log", Time: Tue Apr 3 14:52:25 2007
(==) Using Config File: "/etc/X11/xorg.conf"
[B]Error: API mismatch: the NVIDIA kernel module has the version 1.0-7184, but this xmodule has the version 1.0-8776. Please make sure that the kernel module and all NVIDIA driver components have the same version.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernal module! Please Ensure
(EE) NVIDIA(0): that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0): that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0): Please consult the NVIDIA README for details.
(EE) NVIDIA(0): ***Aborting*
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
XIO: Fatal ID error 104 (connection reset by peer) on X server ":0.0"
       After 0 requests (0 known processed) with 0 events remaining [/B]

Obviously, not being able to load the GUI makes it practically impossible to use ubuntu feasibly... I wouldn't be able to ask this if I didn't have a mac. I'm thinking the line about the "API mismatch" is the important part, now that I have downloaded the drivers, but I have no idea how to make them compatible.

---

### Post by Zuuswa on 2007-04-03
try they command 
```
sudo dpkg-reconfigure xserver-xorg
```
and answer the questions, hopefully that will ressurect your X window system, and from there you can continue to install proprietary drivers if youd like

---

### Post by Feba on 2007-04-03
How do I mark the selections on "Video modes to be used by the X server:"? I tried hitting enter last time, and i think it just skipped them, which left me with small screen res.

I tried running it anyway, it still gives me the same error.

---

