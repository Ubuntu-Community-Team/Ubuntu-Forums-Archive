---
title: "I need help to see my Windows files"
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by yosarian on 2006-11-06
I have 3 partitions, a disk C which is partition in 2 to have Windows and Unbuntu 6.10 and another disk D where I keep all my data.

I can not access to D (neither to C windows) using Ubuntu.

Can someone explain me in detail (tell me what software use to modify the options, etc) how to see the other partition?

Thanks

---

### Post by Iarwain ben-adar on 2006-11-06
Hi,
can you post the output of this command?
```
sudo fdisk -l
```
Note that the -l is a lowercase L.


Iarwain

---

### Post by housam on 2006-11-06
Hi, try this link :
[https://help.ubuntu.com/community/Mo...dowsPartitions](https://help.ubuntu.com/community/Mo...dowsPartitions)

---

### Post by Iarwain ben-adar on 2006-11-06
Hi housam,
i think i need to see some more of the ubuntu pages..

Btw, this is the correct link:
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)


Iarwain

---

### Post by yosarian on 2006-11-07
This is the sudo fdisk-l

> Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1131     9084726    c  W95 FAT32 (LBA)
/dev/hda2            2489        9964    60050970    f  W95 Ext'd (LBA)
/dev/hda3            1132        2488    10900102+  83  Linux
/dev/hda5            2551        9964    59552923+   b  W95 FAT32
/dev/hda6            2489        2550      497952   82  Linux swap / Solaris


The one I want is the number 5.
Can someone explain me in detail how to get there using the Ubuntu 6.10.
Thanks

---

### Post by yosarian on 2006-11-07
I follow the instructions in the link above and I can see my Windows folder, thanks

---

