---
title: "Live CD Problems"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by Five_Iron_OBrien on 2007-10-10
So I have an Ubuntu 7.04 Live CD and it works when I put it into a school desktop computer but when I put it in my laptop and click on the install/try ubuntu button thing.  Then it takes forever to load anything and after like 20-30 minutes it finally says 

 "There was an error starting the GNOME Settings Daemon."

Any Help?

---

### Post by dptxp on 2007-10-10
RAM problem, you have 256 MB or less RAM. 512 MB is OK
Make a SWAP partition of 512 MB to 1 GB with GPARTED first.
Live CD will run and you will be able to install.
Ubuntu runs OK if you have 256 MB RAM.

---

### Post by Five_Iron_OBrien on 2007-10-10
I have 256 of ram

---

### Post by dptxp on 2007-10-10
> **Five_Iron_OBrien said:**
> I have 256 of ram

Yes, that is the problem.[COLOR="Red"] LIVE CD does not run with 256 MB RAM[/COLOR]
Either use alternate CD to install or make swap partition first as suggested.
You can make other partition too with Gparted .
You will find some useful info/ links on my signature.
Both on Gparted and alternate CD.

---

