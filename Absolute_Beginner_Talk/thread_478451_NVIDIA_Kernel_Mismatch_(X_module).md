---
title: "NVIDIA Kernel Mismatch (X module)"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by kasperbs on 2007-06-19
I have followed [a guide]("http://en.wikibooks.org/wiki/NVidia/TV-OUT") to enable tvout on my nvidia card. and I'm getting this error when I'm running the command mentioned underneath. How do I fix this?
> sudo X :1 -layout tv
Give this error
> _XSERVTransSocketOpenCOTSServer: Unable to open socket for inet6
_XSERVTransOpen: transport open failed for inet6/rudolf-desktop:1
_XSERVTransMakeAllCOTSServerListeners: failed to open listener for inet6

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux rudolf-desktop 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686
Build Date: 04 April 2007
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Tue Jun 19 17:25:27 2007
(==) Using config file: "/etc/X11/xorg.conf"


Error: API mismatch: the NVIDIA kernel module has the version 1.0-7184, but
this X module has the version 1.0-9631.  Please make sure that the kernel
module and all NVIDIA driver components have the same version.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

---

### Post by lazyart on 2007-06-19
sudo apt-get install nvidia-glx-new

---

### Post by kasperbs on 2007-06-19
Are you sure. It's not because my nvidia card is new. GeForce4 Ti 4200 AGP 8x

EDIT: The nvidia-glx-legacy driver worked fine except that tvout won't work under it

---

### Post by kasperbs on 2007-06-19
Have you got any suggestions to what I could do instead of installing the newwest nvidia driver and just stick yo the glx.

Meaning I want to upgrade from legacy to glx

---

