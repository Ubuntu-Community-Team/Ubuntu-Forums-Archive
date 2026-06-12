---
title: "seeing all partitions"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by tchoklat on 2007-01-10
This is my HDD

[SIZE=3]tony@tony:~$ sudo fdisk -l[/SIZE]
[SIZE=3]Password:[/SIZE]

[SIZE=3]Disk /dev/hda: 80.0 GB, 80026361856 bytes[/SIZE]
[SIZE=3]255 heads, 63 sectors/track, 9729 cylinders[/SIZE]
[SIZE=3]Units = cylinders of 16065 * 512 = 8225280 bytes[/SIZE]

[SIZE=3]   Device Boot      Start         End      Blocks   Id  System[/SIZE]
[SIZE=3]/dev/hda1   *           1        5773    46371591   83  Linux[/SIZE]
[SIZE=3]/dev/hda2            7823        9599    14273752+  83  Linux[/SIZE]
[SIZE=3]/dev/hda3            5774        7822    16458592+  83  Linux[/SIZE]
[SIZE=3]/dev/hda4            9600        9729     1044225   82  Linux swap / Solaris[/SIZE]
[INDENT]
[SIZE=3]Partition table entries are not in disk order[/SIZE]
[/INDENT]
hda1 is Ubuntu
hda2 is Sabayon
hda3 is a new mounted ext3 partition for data
hda4 is a swap partition


Question: How to I read and wrote to the non-ubuntu partitions. In Sabayon using Konquerer I can see the Ubuntu partition. What application do I use to do this in Edgy?

tchoklat

---

### Post by Bachstelze on 2007-01-10
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by bodhi.zazen on 2007-01-10
sudo chmod 777 /mount/point

---

