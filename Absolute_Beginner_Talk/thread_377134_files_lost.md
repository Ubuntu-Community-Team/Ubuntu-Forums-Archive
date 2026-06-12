---
title: "files lost"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by ar458 on 2007-03-05
My hard drive has 3 partitions. I have windows (NTFS) in the first partition, ubuntu (Ex3) on the second and I am sharing the third partition (vfat). 

Now when I paste something from the Ex3 partition to the vfat partition using ubuntu and try to get it from windows, they are lost. I can't even get them when I boot back from ubuntu.  Is there any way I can fix this and get back the lost files?

---

### Post by moshuptrail on 2007-03-05
If you don't perform an orderly shutdown when switching from Ubuntu to XP, it could be leaving all the data you think you dropped onto the vfat drive in cache.  Before you shut down to switch, open a terminal, and type sync ; sync then shut down.

I'm pretty much guessing, but I've had a similar problem with USB memory sticks.

p.s. you should not normally need to type the sync command - it should be part of an orderly shutdown.

---

