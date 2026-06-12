---
title: "Share an external drive"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by brandon333 on 2007-12-23
How can I Share my 2 partitions, 1 being macosx, other ubuntu, and how can they both share my external maxtor hd hooked yp with firewire?

---

### Post by blueridgedog on 2007-12-23
Do you mean share an external hard drive with other computers/users on a network or share the external hard drive between two OS's?

---

### Post by brandon333 on 2007-12-23
between os's , later on another computer, well actually a ps3...but right now the os.s

---

### Post by blueridgedog on 2007-12-23
The first step in sharing  a hard drive between two OS's is to pick a filesystem that they share in common. in This case, the mac and Ubuntu should be able to read fat32 (potentially others, but I am not a mac person).

If you attached the drive and power it on, you should be able to create a  fat32 partition on the drive with gparted:

System -> Adminstration -> Partition Editor

Be careful when using gparted, you do not want to destroy a working partition.

---

