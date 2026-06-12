---
title: "Pismo Powerbook"
date: 2007-05-23
forum: Apple PPC Users
---

### Post by Pizarro on 2007-05-23
I have a 400 Pismo with 1gb ram 60gb hd and a slot drive dvd/cd drive. It is running Tiger. I have booted off the live cd and Ubuntu loads (although the desktop needs sorting, i have a desktop then a space then the beginnings of a duplicate desk top.) I dual boot my windows desk top with no problem but do not know how to install on the mac to dual boot. Any links to how to would be appreciated.

---

### Post by pxwpxw on 2007-05-23
Use the Alternate install CD version, less problems with the display for installing, and more flexible to sort problems. There is documentation on the install CD iso.

Good place to start -

[https://help.ubuntu.com/](https://help.ubuntu.com/)

[https://help.ubuntu.com/6.10/](https://help.ubuntu.com/6.10/)

Installation Guide (for alternate CD, not for desktop CD) - for i386, amd64, powerpc, sparc, hppa, ia64

and:

[https://help.ubuntu.com/7.04/](https://help.ubuntu.com/7.04/)

And search the forum for "pismo" and "yaboot" should get some hints.

Ubuntu installs yaboot for dual booting (macosx/ubuntu).

Also: 

[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

---

### Post by Pizarro on 2007-05-23
Does the alternate cd run as a live cd ?

---

### Post by pxwpxw on 2007-05-23
No, thats the idea - to avoid having to run the full graphical desktop in the initial install.
Later on you can use a live cd to fix problems in the installed system

---

### Post by Pizarro on 2007-05-23
So do I just put the disk in and follow the instructions ..........and get dual boot ? Don't want to loose my mac stuff. Nothing critical but re-installing would be a pain.

---

### Post by stmiller on 2007-05-23
You have to prepare your machine for a dual boot first, same as you would do on a PC with Windows and Linux. There are programs that will non-destructively resize HFS+ (OS X) partitions to make room for Linux. I believe one is the Gparted live cd- though I'm not sure if it boots on Mac hardware.

The best trouble free thing is to first back up ALL of your data, and start new with the OS X install disc, and when it boots to install OS X, first choose the disc utility at the top of the screen. Then make 2 partitions. Format the first for OS X, and leave the remaining partition unformatted. Then install OS X as usual.

Then put in the Ubuntu disc and run the installer, choose manual for partitioning, and make sure to install in the free unformatted free space. It will install ubuntu in that remaining partition.

Then you can edit the file /etc/yaboot.conf (see PPCFAQs below) as needed.

---

