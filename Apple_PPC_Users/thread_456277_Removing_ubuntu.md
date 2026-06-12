---
title: "Removing ubuntu"
date: 2007-05-27
forum: Apple PPC Users
---

### Post by tx_sumo on 2007-05-27
So it's time for me say goodbye to Ubunutu.  It's not a good fit for my environment, I work in an apple shop and have nothing but macs at home formatted in HFS+ So I am unable to access drives and such.  Also not having flash and JRE doesn't help.  So I put in my CD to reinstall OS X,  and I run into a problem, I can't get my G4 powerbook to boot off of CD.  Here's what I've tried: holding "C" down at boot up, I've tried booting off of the open firmware using the boot-cd command, and also resetting the firmware then trying to boot using the "C" command.  is there a coomand inside ubuntu I can use to force it to understand HFS+ and boot off the CD?

Regards
Sumo

---

### Post by stmiller on 2007-05-27
There is JRE for PPC Linux. And also Linux can read/write to HFS+ drives natively. You can also browse OS X network shares easily (just enable 'windows sharing' in the network prefs of OS X). The networked computers show up in gnome's network view under Nautilus. You can also easily share files/folders from Ubuntu with other OS X users (In gnome- right click on a folder, and click 'share'.)

Aside from all of that,
Have you tried resetting the pram? You might try an OS X forum.

---

### Post by 3rdalbum on 2007-05-28
You don't need to do anything in Ubuntu to get the computer to boot from the CD. Booting is performed by the Open Firmware BEFORE any operating system loads.

Have you checked Apple's knowledge base documents? You should zap the NVRAM (which I believe is Command-Option-N-V on startup) as this holds the information about what partition to start booting from.

---

