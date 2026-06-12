---
title: "[SOLVED] BitPim does not work for Motorola V323i...what does?"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by arvevans on 2008-02-11
Is there a way to make "bitpim" recognize my Motorola v323i cellphone?  Or, is there any Linux software that will work with this unit?

lsusb recognizes that it isconnected:

[INDENT]arv@arv-desktop:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 021: ID 22b8:2ac2 Motorola PCS 
Bus 002 Device 019: ID 093a:2468 Pixart Imaging, Inc. Easy Snap Snake Eye WebCam
Bus 002 Device 018: ID 046d:c03d Logitech, Inc. 
Bus 002 Device 003: ID 0451:1446 Texas Instruments, Inc. TUSB2040/2070 Hub
Bus 002 Device 001: ID 0000:0000  
arv@arv-desktop:~$ 
[/INDENT]

This unit does not have a removable memory chip.  No, it is not recognized as a mass storage device.

Thanks,

Arv

AMD 64X2-3800, 1GB RAM, 160 GB HD, Ubuntu 7.10 Gnome.

---

### Post by arvevans on 2008-02-13
OK.  Seems that nobody has a solution for this, so I'll mark it CLOSED and work on my own fix.

Arv
_._

---

### Post by rab4567 on 2008-02-13
Hey I've been there I have a Samsung sch-u740

1.) Go to bitpim.org download the latest debian pacage version 1.0.5.0

2.) Plug in the usb cable to your phone then go to applications> accessories> terminal type lsusb and enter. You should see a string of driver listed thats a good sign.

3.)Then type in terminal sudo bitpim enter then your password and you should get a conformation box stating it recognizes your phone then type in your name and phone model.

Good Luck

---

### Post by arvevans on 2008-02-14
Thanks, but I've already been there and already done that. 

 I even programmed in the major & minor nodes for the USB net address.  This let bitpim see that there was a phone at that address, but it still will not talk to it.

Seems that the Motorola V323i is a bit of an oddball case in that it apparently does not use the same interface commands as the rest of Motorola products.  That is unfortunate because it has almost any function that I could want, except for talking to Linux.

Since I boughtand paid for this phone once, I have a strong aversion to paying Motorola for it again in the form of their $40.00 software package for it to talk to Microsoft OS systems.  Seems that it is cripple-ware if they provide it without the software to make it work.

I'm a programmer but one with limited time to devote to decoding the interface commands by myself.  If someone knows the specific interface commands for the Motorola 323i, i would be appreciative of seeing them.

Thanks,

Arv
_._

---

