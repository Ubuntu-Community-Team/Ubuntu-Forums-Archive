---
title: "help me on these topics.........plz"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by saurabh kakkar on 2007-07-05
hi
   every time i log into ubuntu 7.04 i have to mount my FAT32 partions from  
   PLACES->COMPUTERS is there any way so that these partions will mount automatically  after ubuntu stars.  
                          also
how can i format my pendrive ?what will be its file system after format ? plz help..   

```
sudo fdisk -l
``` gives this results   

> Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   c  W95 FAT32 (LBA)
/dev/sda2            2551        9130    52853850    f  W95 Ext'd (LBA)
/dev/sda3            9131        9733     4843597+  83  Linux
/dev/sda5            2551        5100    20482843+   b  W95 FAT32
/dev/sda6            5101        7650    20482843+   b  W95 FAT32
/dev/sda7            7651        9095    11606931    b  W95 FAT32
/dev/sda8            9096        9130      281106   82  Linux swap / Solaris

---

### Post by PaulFr on 2007-07-05
1. You will need to add all the Windows partitions to your /etc/fstab file (see **[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)** for details).

2. To create a DOS FS on your pendrive, you need **mkdosfs**. To check your pendrive for errors, you can use **dosfsck** - check their man pages for details.

---

### Post by coolen on 2007-07-05
For formatting:
```
sudo apt-get gparted
```
Fire it up from System -> Administration -> Gnome Partition Editor.
From there, select your pen drive. It'll probably be the last entry, and will probably be a lot smaller than your other partitions (although technology these days...). You could verify it using unused space and such through Nautilus...doubt it'd show up in fstab.
Then right click, go to Format, and select the filesystem you want. If you'll be taking it to a Windows machine, you'll want fat32...actually, you'll probably want it regardless. FAT's phat, yo.

Actually, seeing your output, it's already fat. Why do you want to format it?

---

