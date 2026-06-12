---
title: "Buring a live boot CD for linux"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by the.ubiquitary on 2007-10-27
I'm trying to figure out how to burn a live boot cd for a friend of mine that wants to try linux, but I know its not simple, something about putting the iso image on the cd, but im totally lost. Can someone tell me if there is a program or command or something that does it?

---

### Post by Daveth on 2007-10-27
try

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by the.ubiquitary on 2007-10-27
Thanks

---

### Post by the.ubiquitary on 2007-10-27
Actually, is there a way to basically put that image on something like an ipod so they can install from the ipod as opposed to using a cd?

---

### Post by mdpalow on 2007-10-27
It's a lot more simple than you think. :)

Click APPLICATIONS -> SOUND & VIDEO -> K3B

 If you didn't install K3b, go to SYSTEM -> ADMINISTRATION -> SYNAPTIC PACKAGE MANAGER and search for K3B and install it. Then:

Click APPLICATIONS -> SOUND & VIDEO -> K3B

At the bottom of K3B click on BURN CD IMAGE
Select the file you want to burn and click BURN

Done


Good luck,

---

### Post by candtalan on 2007-10-27
> **the.ubiquitary said:**
> Actually, is there a way to basically put that image on something like an ipod so they can install from the ipod as opposed to using a cd?

It really is not difficult to burn the iso image to a CD, and it is further easier because the PC will easily be able to boot and run and install from the CD, however, it might not from a usb device. 

The reason the image burn to cd seems strange is probably because your burning software is not usually expecting you to do that. As a (windows?) customer, you will be expected to only purchase CDs that a manufacturer has sold to you! Burning the iso image may be the first move you make towards real freedom!

The main trick to be aware of is to find and use burn the *image* (and not 'make an iso') this choice will be somewhere in your burning menus.

There is a small chance that the download or the burn itself might not be perfect  enough, but if you burn at say half the rated speed you will have a good chance first time.. With the live cd the first menu at booting includes an option to check the cd. Use this, it will verify several things, including that your target drive can read the cd now.

I understand that an easy way to install is to use wubi - via windows and into a windows folder. This does not use a new partition, and the systems remain in a windows file system, but it is a real install:
[http://wubi-installer.org/](http://wubi-installer.org/)
and
[http://crunchgear.com/2007/10/25/wubi-super-easy-linux-installation/](http://crunchgear.com/2007/10/25/wubi-super-easy-linux-installation/)

hth

---

### Post by bliffle on 2007-10-27
On my ubuntu system I could burn the iso directly frm the file manager just by right-clicking on the iso name and making the correct selection. No other program required.

---

