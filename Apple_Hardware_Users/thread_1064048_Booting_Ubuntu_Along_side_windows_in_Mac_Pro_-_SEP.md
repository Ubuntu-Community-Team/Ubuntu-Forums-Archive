---
title: "Booting Ubuntu Along side windows in Mac Pro - SEPERATE HDDs"
date: 2009-02-08
forum: Apple Hardware Users
---

### Post by FendersRule on 2009-02-08
Hi!

All of the tutorials online gave directions for OSs sharing the same partition.

I have 4 HDDs in my Mac Pro right now. 2 of them are set up for RAID in OSX.

The other one I successfully installed Vista via Bootcamp.

The third one, I installed Ubuntu on (not through bootcamp).

However, in my Mac's firmware boot, and in OSX startup disk, the Ubuntu drive does not show...

Question is, what do I need to do for triple booting with separate HDDs?

---

### Post by cyberdork33 on 2009-02-09
This issue is not well understood.
First you will probably need to sync the partition tables on that disc somehow.
Then you need to figure out how to setup the bootloader to properly boot Linux.

[http://wiki.debian.org/DebianOnIntelMacPro#line-187](http://wiki.debian.org/DebianOnIntelMacPro#line-187)

---

