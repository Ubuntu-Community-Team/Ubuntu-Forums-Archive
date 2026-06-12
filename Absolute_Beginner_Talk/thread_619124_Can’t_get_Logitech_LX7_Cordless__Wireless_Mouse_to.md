---
title: "Can’t get Logitech LX7 Cordless / Wireless Mouse to work on Gutsy"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by snideatlondon on 2007-11-21
I had posted the following request on the General Help forum but didn’t get a single reply. I hope someone here can point me in the right direction – thanks:

I am trying to get my Logitech LX7 cordless mouse work on Ubuntu Gutsy. While my standard PS/2 mouse was recognised during installation, LX7 wasn't.

lsusb shows a "Logitech, Inc. MX-1000 Cordless Mouse Receiver" in one of the ports but I have no response at all from the cordless mouse which works perfectly when I plug it into my Windows XP box. 

(full lsusb output is attached below)

sudo cat/dev/input/mice produces an output from the PS/2 mouse but nothing for LX7.  

similarly, sudo cat/dev/input/mouse1 only sees the PS/2 mouse. sudo cat/dev/input/mouse0 produces no output from either mouse.

dmesg reports something about "usb 2-3: usbfs: USBDEVFS_CONTROL failed cmd hald-addon-usb- rqt 192 rq 9 len 8 ret -62" but I have no idea what this means. 

(dmesg output is attached)

(copy of xorg.conf is also attached)

I would be very grateful for some help. I am new to Linux and this is driving me round the bend.

thanks very much

Ubuntu 7.10
Kernel Linux 2.6.22-14-generic
GNOME 2.20.1[/FONT]

---

