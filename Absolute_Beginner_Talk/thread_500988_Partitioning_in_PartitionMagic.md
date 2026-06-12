---
title: "Partitioning in PartitionMagic"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by squidsta711 on 2007-07-14
I set aside 25 gb for ubuntu because I still want to boot windows. When creating partition type I can select from: FAT, FAT32, NTFS, Linux Ext2, Linux Ext3, and Linux Swap. Basically, I have no idea what I'm doing, but in the end I want to be able to dual boot Windows XP, and Ubuntu.

---

### Post by bobplano on 2007-07-14
you need an ext3 partition for the main part of ubuntu (in the installer you need to mount it to / ), and a linux-swap partiton to hold spill-over from the RAM. you should probably make it 24gb for / (the ext3 partiton) and 1gb for linux-swap

---

### Post by smoker on 2007-07-14
hi, i would make a 24GB partition for you main ubuntu install, and a 1GB swap partition, and when you run the install, select these partitions for the install /, and the swap

best of luck

---

### Post by ugm6hr on 2007-07-15
> **squidsta711 said:**
> Basically, I have no idea what I'm doing, but in the end I want to be able to dual boot Windows XP, and Ubuntu.
If you are unsure about partitioning - it is easiest to leave an unpartitioned space (25GB in your case), and let the Ubuntu installer do the partitioning for you.  Just pick the ***Guided Install - use largest continuous free space***, and it'll do the work for you.

Just one thing to consider - make sure you do not have more than 2 partitions+25GB free space.  If you do - create a single 25GB *extended* (rather than primary) partition, but no partitions within it.  Then follow instructions above.

---

### Post by dptxp on 2007-07-15
Choose manual partitioning while installing Ubuntu. Resize the 25 GB to 6 GB for / (root) ext3 format. Resize rest to 18 GB for /home (ext3). Keep 1 GB for SWAP.

The separate /home will store your data and you shall be able reinstall in / without disturbing data whenever reinstall is needed.

---

