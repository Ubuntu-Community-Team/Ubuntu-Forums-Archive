---
title: "kernel not copatible??"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by tygr88 on 2007-10-08
i tried to install nvidia driver for my card ........after it started it told me that the kernel i was running was different form what it supported but i installed any way(i kno that was stupid).....ne ways now it gives me some error whenever i try i type startx.....how do i uninstall the driver??

---

### Post by tygr88 on 2007-10-08
this what it exactly says


```
X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux Kunniasta 2.6.20-16-generic #2 SMP Fri Aug 31 00:55:27 UTC 2007 i686
Build Date: 04 April 2007
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Oct  2 23:13:24 2007
(==) Using config file: "/etc/X11/xorg.conf"

Error: API mismatch: the NVIDIA kernel module has the version 1.0-7184, but
this X module has the version 1.0-9755.  Please make sure that the kernel
module and all NVIDIA driver components have the same version.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly.
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 0 requests (0 known processed) with 0 events 
```

---

### Post by 5-HT on 2007-10-08
I'm assuming that you used nvidia's own installer? To uninstall you can pass '--uninstall' to the installer. 
The problem is that the nvidia driver requires a kernel interface layer and yours is mismatched with the actuall driver itself. Nvidia's installer will automagically take care of the kernel layer unless you already have it installed...my guess is that you may have nvidia-kernel-common at a different version than the driver installed from the repos.

To rectify, either:
I. Use both the nvidia module and nvidia-kernel-common available in the repos
II.  Remove nvidia-kernel-common and let the nvidia installer configure everything for you.

Note that you'll either needto edit your xorg.conf to stipulate whether you'd like to use the nvidia  module or  the  default  nv  (2d, opensource drivers) or let nvidia's xconfig utility take care of it for you.

cheers,

---

### Post by tygr88 on 2007-10-08
pls i am new to ubuntu...........so pls tell me how to rectify the prob in laymans language

---

### Post by PmDematagoda on 2007-10-08
To solve your problem as 5-HT says you can either do:-

1) Install the nvidia-driver in the repositories using "sudo apt-get install nvidia-glx-new" if you have a fairly new card or "sudo apt-get install nvidia-glx-legacy" for old VGA cards.

or

2) First remove nvidia-kernel-common using the command:-

```
sudo apt-get remove nvidia-kernel-common
```

And then retry installing the nvidia driver and allowing it to set it's own kernel. After installing the nvidia driver, reconfigure X using:-

```
sudo dpkg-reconfigure xserver-xorg
```

And choose nvidia as the driver, if that doesn't work choose the open-source driver for nvidia which is nv. Just go along that configuration leaving things you don't know about in their default values but if you think something is wrong then you can rectify that mistake.

After you successfully configure X, start X using:-

```
startx
```

---

