---
title: "adding hfsplus pacage to livedisk"
date: 2009-11-28
forum: Apple Hardware Users
---

### Post by itachis.eyes on 2009-11-28
ok i'm not actually using apple here but i figured that most people asking how to add support for mac partitions to there livedisk would be asking here (thus better chance of answer)

i need to format some hard drives to hfs+ but macintosh being the "prodigy OS" that it is fails to recognize anything but its own hfs and hfs+ partitions and will not format disk to said partitions.
so i need to add the "hfsplus" package to my ubuntu livedisk but:
i ran ```
sudo apt-get install hfsplus
``` and also had the dependencies installed but when i open gparted it still "grays out" the hfs and hfs+ options 

am i doing this right? or is there another way to get macintosh partition support onto my livedisk?

---

### Post by tiresia on 2009-11-28
The Linux Kernel is able to read HFS/HFS+/HFS+ Journaled - without need to add any packages. But there is no way to generate an Apple HFS. You can shrink an Apple HFS/HFS+ (not Journaled) with gparted, but you can't create it.

---

