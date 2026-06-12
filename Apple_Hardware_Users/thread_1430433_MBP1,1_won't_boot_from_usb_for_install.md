---
title: "MBP1,1 won't boot from usb for install"
date: 2010-03-15
forum: Apple Hardware Users
---

### Post by Snabbdist on 2010-03-15
Model:	MacBookPro1,1
Intel Core Duo 2,16 GHz (32 bit)
OS X 10.6.2
Boot ROM-version: MBP11.0055.B08
SMC-version (system):	1.2f10
2 gb ram

I've tried this guide: [https://help.ubuntu.com/community/Installation/FromUSBStick#Copying Files to USB Stick]("https://help.ubuntu.com/community/Installation/FromUSBStick#Copying Files to USB Stick")

with both the standard 9.10 32 bit cd and the netbook remix.
when I try to boot and hold alt the only partition that appears is the os x one. so no usb.

the cd reader is broke. that's why I'm trying via usb.

edit: its a usb stick btw, 16 GB that I'm trying to boot from.

---

### Post by linuxopjemac on 2010-03-15
you could follow this link:

[http://mac.linux.be/content/installation-ubuntu-karmic-koala-macbook-pro-31-usb-stick-0](http://mac.linux.be/content/installation-ubuntu-karmic-koala-macbook-pro-31-usb-stick-0)

---

### Post by Snabbdist on 2010-03-15
> **Snabbdist said:**
> 
the cd reader is broke. that's why I'm trying via usb.

[QUOTE=linux.be]
-Re-insert burned Ubuntu disc and shut down.[/QUOTE]

unfortunately I can't insert anything into the cd drive. I can burn via my other computer but nothing can be put inside the mac.

---

### Post by linuxopjemac on 2010-03-15
then do those things from another computer with Ubuntu, easy, or not?

---

### Post by Snabbdist on 2010-03-15
hm ok. i think ive tried that before... but maybe i only tried the wubi installer then, from windows. ill just try to install ubuntu on the usb from the usual ubuntu boot cd installer then... and boot from that. 
I thought the mac needed some kind of editing to a bootfile inside os x to be able to boot ubuntu/ubuntu-cd from usb...?

will i be able to install ubuntu to an internal drive partition from the usb? or do i have to always boot from usb?

anyways ill report back what i find out

---

### Post by Snabbdist on 2010-03-15
> **linuxopjemac said:**
> you could follow this link:

[http://mac.linux.be/content/installation-ubuntu-karmic-koala-macbook-pro-31-usb-stick-0](http://mac.linux.be/content/installation-ubuntu-karmic-koala-macbook-pro-31-usb-stick-0)

got as far as this:
[http://i42.tinypic.com/r8f67r.png]("http://i42.tinypic.com/r8f67r.png")

where it says "dont use this partition", i couldn't choose "EFI Boot Partition". is "us as: FAT32 File System" good enough?

strange! I'm using the 9.10 cd...

---

