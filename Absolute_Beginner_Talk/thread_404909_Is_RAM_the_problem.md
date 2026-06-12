---
title: "Is RAM the problem ?"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by dptxp on 2007-04-09
Ubuntu 6.10 Edgy Eft and7.04 Feisty Fawn (Herd 5), both 64-bit, say that unable to load Gnome properly and sort of hang with live CD. With 32-bit 6.10 I reach the desktop but the CD access continues and system is dead slow.

I am running Ubuntu on laptop. But on this desktop (AMD Sempron 2500+ 64-bit, Asus MOBO with via chipset, 256 MB RAM) I have yet to succeed.

64 MB of the 256 MB RAM is used as video shared memory. 192 MB left. Is that the problem?

---

### Post by siciliancasanova on 2007-04-09
I'm quoting this from the bottom of [this page]("http://www.ubuntu.com/products/whatisubuntu/desktopedition").

> Ubuntu is available for PC, 64-Bit and Mac architectures. CDs require at least 256 MB of RAM. Install requires at least 2 GB of disk space.

---

### Post by jvc26 on 2007-04-09
By the looks of it yes, you need at least 256 (as mentioned above). If you want to install try using the alternate install cd as that allows you to install with slightly less RAM. (As it isnt a livecd)
Il

---

### Post by dptxp on 2007-04-09
When I try to run live CD on Sempron 2500+, 256MB RAM, SATA, no RAID, AsusK8V-MX MOBO, Via k8M800 and VIA VT8237R chipsets, desktop does not open.
I am listing my problem here, I do not think that RAM is the problem, this problem is there in bug reports elsewhere. I do not want to go for alternate CD unless that is the only solution as that cannot be run live.


Tried with 64bit 6.10, 7.04 Herd-5, used options pci=noacpi, noapic nolapic, problem stays.

Tried with CDROM as Primary Master, Secondary Master.


Same message :

[COLOR="Red"]There was an error starting the Gnome Settings Daemon.
Somethings such as themes, sounds and background settings may not work properly.[/COLOR]

There is more in the message.
Well, nothing starts after that.


With 32-bit 6.10, I get the desktop, but nothing seems to work.
Even SimplyMepis 6.5 , 64-bit is dead slow, nothing seems to work even on default desktop.

I have run the Ubuntu Cds (the 64 bits) fine on my laptop.

---

