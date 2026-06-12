---
title: "Disks (Disc Manager)"
date: 2005-11-12
forum: Absolute Beginner Talk
---

### Post by topic58 on 2005-11-12
Hi, I have 4 partitions with NTFS. I have now been copying all data from them into a USB2-disc (Lacie). My question now is - can I format my 4 NTFS-partitions with Disks into FAT32? Using Ubuntu 5.10. OR do I need some files from Synaptic making Disks capable of helping me with this task? (I noticed there were som files for download in Synaptic for working with NTFS.) If Disks is capable of this task, I want to use it here. :???:

---

### Post by apjone on 2005-11-12
[QUOTE=topic58]Hi, I have 4 partitions with NTFS. I have now been copying all data from them into a USB2-disc (Lacie). My question now is - can I format my 4 NTFS-partitions with Disks into FAT32? Using Ubuntu 5.10. OR do I need some files from Synaptic making Disks capable of helping me with this task? (I noticed there were som files for download in Synaptic for working with NTFS.) If Disks is capable of this task, I want to use it here. :???:[/QUOTE]
open a terminal and type the following commands and read the output , to exit a man page press 'q'

1) man fdisk

2)man parted

3)man mkfs

that should help you

If you learn it yourself it is more satisfing.

---

### Post by topic58 on 2005-11-12
Fixed my problem by using GParted. All 4 NTFS partitions are now in vfat (FAT32). I guess I could have used fdisk, but I am still pretty new to this. Better safe than sorry. But still thanks a lot. :smile:

---

