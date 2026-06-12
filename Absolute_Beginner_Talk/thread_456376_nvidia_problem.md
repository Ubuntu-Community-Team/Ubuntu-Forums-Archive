---
title: "nvidia problem"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by fanderal on 2007-05-27
Hi,

Learned about Ubuntu and loaded Feisty 10 days ago on a partitioned HD. No problems in making the liveCD or installing the system. Real nice default layout and desktop. Boot time is about the same for Ubuntu as XP, but the programs load and run speedier in Ubuntu. I've got a 2002 Gateway P4, 2.0GHz with XPHome, SP2. My graphics card is an NVIDIA GeForce2 MX 100 with 32MB. 

The LiveCD loaded these packages - 
nvidia-glx (1.0.9631+2.6.20.5.15.20)
nvidia-kernel-source (1:1.0.9631+2.6.20.5-16.28) 
xserver-xorg.video-nv (1:2.0.0-0ubuntu3) 

The problem is whether I Suspend or Hibernate the system for 5 minutes or several hours, the screen doesn't work/refresh. Its black and halfway filled with a bunch of tall, white, smilie zeros. I found nothing to adjust in Preferences and Administration. The forum threads discussing Nvidia didn't appear to address this problem. I looked through the Synaptic Package Mgr and from the nvidia-glx-legacy info, figured this package might fix it. I went to the Nvidia site and sure enough, the older cards (like I have) are listed on their Legacy page. 

Using the Synaptic Pkg Mgr, I installed the recommended packages - 
nvidia-glx-legacy 
nvidia-legacy-kernel-source (1.0.7184+2.6.20.5-16.28) 
nvidia-settings 

When I rebooted I got this page - 
>  
X Window System Version 7.2.1 
Release Date: 22 Jan 2007 X Protocol Version 11, Revision 0, Release 7.2 
Build Operating System: Linux Ubuntu Current OS: Linux mydisk 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 
Build Date: 04 April 2007 (check with [http://wiki.x.org](http://wiki.x.org) for latest version) 
Module Loader present 
Markers: (--) probed, (**) from config file, (==) default setting, (++) from command line, (!!) notice, (II) informational, (WW) warning, (EE) error, (NI) not implemented, (??) unknown 
(==) Log file" "/var/log/Xorg.0.log", Time: Wed May 23 18.19.58 
(==) Using config file: "/etc/X11/xorg.conf" 
(WW) NVIDIA: No matching device section for instance (BusID PCI:1:0:0) found 
(EE) No devices detected 

Fatal server error: no screen found 

<OK> 
 

I used the Terminal (with some very timely help!) to reload the original packages. The system suggested this command to reset the xserver: "dpkg-reconfigure -phigh xserver-xorg". It loaded "xserver-xorg-vesa" so I got my screen back. And then I reloaded the original "xserver-xorg-nv". But the problem still exists. 

Anyone know how to fix this, or seen it discused and resolved somewhere in the forums? 

Thanks! 

fanderal

---

### Post by AAM on 2007-05-27
when you restart, have you tried the Xwindows three finger salute to restart the X server (Ctrl-Alt-Backspace)?

---

### Post by fanderal on 2007-05-27
> **AAM said:**
> when you restart, have you tried the Xwindows three finger salute to restart the X server (Ctrl-Alt-Backspace)?

Thanks for responding. I tried it but it didn't work. 

I clicked on Suspend, the 'puter and the screen did what they're supposed to do, and when I pressed the space bar to wake it up, I got that dumb screen again. I did the “ Ctrl-Alt-Backspace” and the screen didn't change. I entered my login name and password as if the screen was working, and when I pressed Enter, nothing changed on the screen. I had to manually press the 'puter button to restart the computer. 

Any other thoughts?

---

### Post by AAM on 2007-05-31
no sorry, I have strenuously avoided the suspend/hibernate use on my laptops. Mainly because I started some time ago with linux and it didn't work. I know it is now supposed to be better but I have just not tried to reintroduce that action into my use.

---

