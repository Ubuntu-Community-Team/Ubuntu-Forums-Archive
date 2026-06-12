---
title: "cant find windows partition"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by yuffie8 on 2008-01-27
hey, i feel a bit silly but i cant find my windows partition - i just did a clean install of xp with the intention of starting again but cleaning stuff up and making ubuntu my primary partition.
I fear i may have overwritten xp when then installing ubuntu (which i wouldnt mind keeping as there is some stuff i just cant get wine to work with) ... but alas!

i checked through the other posts but i couldnt find anything to help, cheers

---

### Post by yabbadabbadont on 2008-01-27
Please post the output of running, in a terminal window, the following command:
```
sudo fdisk -l
```

---

### Post by yuffie8 on 2008-01-27
yuffie@yuffie-desktop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9bb1edf4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6082    48853633+  83  Linux
/dev/sda2            6083        6446     2923830   82  Linux swap / Solaris

Disk /dev/sdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe397e397

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4998    40146403+   b  W95 FAT32


hmm that would indicate to me that i have indeed overwritten xp as i see no windows system.

---

### Post by yabbadabbadont on 2008-01-27
What is on your 41.1 GB drive?  (/dev/sdb)  That shows that it has a windows partition on it and nothing else.

---

### Post by yuffie8 on 2008-01-27
I initially installed xp on my 80gig and then installed linux on that HD also, and the other 41.1gig is just a formatted FAT32 which before i started again i had xp and ubuntu on with the 80gig as the FAT32 ... just like spare space through anything in there area.

So i was expecting ubuntu and xp on 80gig and nothing on the 2nd disk

---

### Post by yabbadabbadont on 2008-01-27
Yep, it's gone then.

---

### Post by yuffie8 on 2008-01-28
ok so i started again, installed windows on that 2nd 40.1gig and now have just linux on this, is there any way i can add it to the grub? 

sudo fdisk -l 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9bb1edf4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9352    75119908+  83  Linux
/dev/sda2            9353        9729     3028252+   5  Extended
/dev/sda5            9353        9729     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe397e397

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4998    40146403+   b  W95 FAT32




cheers by the way

---

### Post by bumanie on 2008-01-28
Out of interest why did you choose fat32 for the xp drive?
Secondly, it is possible to get windows to boot via grub from a second/slave hard drive, however the prefered option is to have windows on the first partitionof the primary drive. Check out this link
[http://users.bigpond.net.au/hermanzone/p15.htm#Chainloading_Windows_using_map_commands](http://users.bigpond.net.au/hermanzone/p15.htm#Chainloading_Windows_using_map_commands)

---

### Post by yuffie8 on 2008-01-28
not quite sure why, would you advise i start again on ftns? Cheers for the link, ill check it out in a little while :)

---

### Post by seventhc on 2008-01-28
If you install xp first and leave a free partition for ubuntu, then install ubuntu second. During the install you choose to have ubuntu use the remaining free space. When it finishes installing you reboot and you will have a choice to boot into xp or ubuntu. :)

---

### Post by bumanie on 2008-01-28
That is up to you. The point is that until recently, to share files between windows and linux, one did need a fat32 /share partition. However, since 7.10 version of ubuntu, the ntfs-3g program matured enough to be included in the linux kernel and you can now read and write to ntfs from linux/ubuntu (ntfs-3g can be added to feisty if you are using that). There is also a program that can be installed in windows to allow ntfs to read/write to ext3. Therefore fat 32 is longer necessary. Each OS can now read/write to each other's file system. The choice is your, but fat32 is regarded as being inferior.

---

