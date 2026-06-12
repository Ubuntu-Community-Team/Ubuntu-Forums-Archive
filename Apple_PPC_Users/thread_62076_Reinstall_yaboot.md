---
title: "Reinstall yaboot?"
date: 2005-09-03
forum: Apple PPC Users
---

### Post by sulobanks on 2005-09-03
I would like to try maconlinux to run os x from time to time (like when I want to see a flash movie or something), but I have tiger.  After much googling, I've decided it would be much easier if I just downgraded to panther.  I have a dual boot os x/ubuntu.  I'm pretty sure that installing panther will wipe out my yaboot.  How would I go about downgrading to panther and getting yaboot back to its rightful place?  I would really prefer not to have to redo my entire system.

Here's my partition map:
/dev/hda1     Apple_partition_map Apple                     63 @ 1         ( 31.5k)  Partition map
/dev/hda2         Apple_Bootstrap untitled                2048 @ 64        (  1.0M)  NewWorld bootblock
/dev/hda3         Apple_UNIX_SVR2 swap                  260096 @ 2112      (127.0M)  Linux swap
/dev/hda4               Apple_HFS Apple_HFS_Untitled_2  58342976 @ 262208    ( 27.8G)  HFS
/dev/hda5         Apple_UNIX_SVR2 swap                 2539063 @ 58605184  (  1.2G)  Linux swap
/dev/hda6         Apple_UNIX_SVR2 untitled            56065993 @ 61144247  ( 26.7G)  Linux native

---

### Post by khc on 2005-09-03
After you installed panther, hold down the option key when you boot up the machine, that should let you choose to boot to linux from openfirmware. Once you are in linux, run:

sudo ybin

---

