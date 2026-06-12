---
title: "New Partition Options"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by valros on 2007-12-26
First Question,   Can Kubuntu access files on a seperate partition, if not is their a program that will copy directories to different a partition.

Second Question,   Ive re-sized my old partition and have 10Gigs of free space. When I create a new partition on the free space it gives me these options(below), what should be chosen as the options for this partition to be a secondary partition containing Kubuntu with (hopefully) access to the other, main partition, which is 90Gigs.

Type -
          Primary  /  Logical

New Partition Size - 10026

Location for new Partition -
          Beginning  /  End

Use as -
          ext3
          ext2
          reisefrs
          jsf
          xsf
          fat16
          fat32
          swap
          efi
          <dont use>

Mount Point - Mount point for other partition is /dev/sda1/ from /dev/sda/

What options should be chosen if its possible for Kubuntu to access the main partition.

---

### Post by Moop on 2007-12-26
Yes Kubuntu can access the other partiton and should mount it automatically for you. 

You will want to create a ext3 partition with a mount point of /

---

### Post by valros on 2007-12-26
What type though

Primary or Logical

Beginning or End

---

### Post by Moop on 2007-12-26
Primary partition is the usual but either one will work. The location doesn't really matter as far as i know but I would put it at the end.

---

