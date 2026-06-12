---
title: "gutsy gibbon fails to locate mp3 player."
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by enetic on 2007-10-16
i have a problem with the newest (beta) version of ubuntu. when i try to plug in my mp3 player, it wont pop up on the desktop. the computer acts like nothing has happened. when i type "lsusb" in terminal, i can only find my optical mouse, and nothing else.. whats up with that??

---

### Post by Perpetual on 2007-10-16
Ipod?  Zune?

---

### Post by enetic on 2007-10-17
creative muvo tx.. :P256mb

---

### Post by BOZG on 2007-10-17
Have you tried using Amarok or Banshee to see if they can find it?

---

### Post by enetic on 2007-10-18
yeah.... no program can locate it... . . . wierd..

---

### Post by philinux on 2007-10-18
I know this sounds crazy but just try Gthumb it mounts my mobile phone ! :)

---

### Post by enetic on 2007-10-19
not in my case, but i found out that this is some kind of bug. when i boot ubuntu with the usb cable connected, the phone pops up on the desktop when ubuntu is up and running again. 

when i type lsusb now, i see my phone connected:

$ lsusb
Bus 001 Device 003: ID 046d:c01d Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 0fce:d016** Sony Ericsson Mobile Communications AB **
Bus 002 Device 003: ID 0c45:62c0 Microdia 
Bus 002 Device 001: ID 0000:0000  
$ 

ill try to do a report on this to the ubuntu team asap.

right now there is nothing to do about it, thanks for all your help though.!
EDIT: the same would be the solution for my mp3 player! ....
eNetic..

---

### Post by zero244 on 2007-10-19
Open a terminal window and try this
sudo rmmod ehci_hcd
Password:

It will be gone on the next reboot.......I made a launcher that I keep on my desktop.

---

### Post by enetic on 2007-10-20
thanks :P that worked..

---

### Post by Tuho on 2007-11-06
Thanks!

I had similar problems connecting _any_ usb devices since updating to gutsy. This workaround works for me too. Cheers.

[edit] ...and my usb controller if someones interested.
> username@host:~$ lspci|grep USB
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
username@host:~$ 

---

