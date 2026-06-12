---
title: "partitioning late"
date: 2006-06-19
forum: Absolute Beginner Talk
---

### Post by skale on 2006-06-19
I want to create a, say, 15GB partition for Windows on this computer.

sudo fdisk -l> 
Disk /dev/hda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4675    37551906   83  Linux
/dev/hda2            4676        4863     1510110    5  Extended
/dev/hda5            4676        4863     1510078+  82  Linux swap / Solaris
I would like to create that partition *without* erasing the disk. I know most people do it while installing, but I don't want to lose all the ubuntu files. I believe Windows starts with a little partition window, but I am not sure if it will work.

---

### Post by K.Mandla on 2006-06-19
It might be tricky, but I only say that because I've only ever built dual boot systems by installing Windows first.

There's a partition editor called GPartEd that might help; however, it might not allow you to repartition your Ubuntu drives while Ubuntu is running.

If you can download a small ISO and burn a CD, there's a GPartEd Live CD that boots up without using the hard drive, and will let you modify the partitions to make space for Windows. I've used it more than once and it has saved me plenty of time. It's graphical too.

Of course, all that is use-at-your-own-risk. Make sure you back up anything you can't afford to lose, before you start messing with partitions. :)

---

