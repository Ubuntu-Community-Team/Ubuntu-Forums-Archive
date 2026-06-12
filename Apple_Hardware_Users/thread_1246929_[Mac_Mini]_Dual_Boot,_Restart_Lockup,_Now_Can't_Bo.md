---
title: "[Mac Mini] Dual Boot, Restart Lockup, Now Can't Boot ANYTHING!"
date: 2009-08-22
forum: Apple Hardware Users
---

### Post by BDPNA on 2009-08-22
I could really use some help here as this has happened twice now on two different hard drives, so I know it's not a fluke.

I set up my Mac Mini for a dual boot setup, using the common guides to split hard drive into 2 partitions (windows and osx) and let Ubuntu do the rest.

Both times I used rEFIt as the boot manager, but the second time after I synced the partition tables, I removed it and just had the machine boot into Ubuntu by default.

Anyway, Ubuntu 9.04 was working great, until I realized what caused the problem BOTH times.  Instead of doing a SHUTDOWN, I tried a RESTART.  As we know, the mini cannot do either under 9.04, but for whatever reason, when you try a restart, something causes your partition tables or mbr to go wacky.  Really wacky.  Now, no matter what I do (option at startup, etc), BOTH partitions will not boot.  I get no bootable device when I select ubuntu, or the NO symbol (circle and line) eventually when I try OSX partition.

How can I fix this?  Note - Booting from CD also does not seem to be working.  Booting from the Ubuntu CD gets to the "ISOLINUX 3.63 copyright" line and just sits there.  I think it's because it absolutely cannot access the hard drive at all.

I know this is not a fluke because the first time it happened, I gave up and put a new hard drive in, and now it's happened again, to this hard drive.  I rebooted 20 times using the "shutdown" command from ubuntu without issue, but the second I picked "restart" instead of shutdown from 9.04 I have an unbootable system.

What can I do?  PLEASE help?  I'm out of ideas.  Pretty frustrating that such a simple thing as a lockup when shutting down can render a hard drive useless TWICE.  Helllp!

---

