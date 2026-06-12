---
title: "External Hard Drive Problem"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by MikeyRibbs on 2007-03-22
Ok, I was trying to install grub bootloader on my external hard drive one day and it didnt work. So I restarted the compy to find that windows was deleted.( I was trying to dual boot using this wierd app thing) So I installed ubuntu. Now, when I plug in my external it doesn't notice that it exists but it does and it is plugged in and on. I think that I need to reset the drive to FAT32 but I don't know how. Can someone please help me out?

---

### Post by george29 on 2007-03-23
with everything plugged in and switch on...

open a terminal and type

```
 sudo fdisk -l 
```

that should list all partitions available whether mounted or not...

your external drive should pop up as /dev/sda1 and it should also tell you what filesystem it has 

then refer to this post  [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

to try and get it mounted.

---

