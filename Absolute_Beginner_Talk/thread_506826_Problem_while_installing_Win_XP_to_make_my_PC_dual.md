---
title: "Problem while installing Win XP to make my PC dualboot"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by pkj on 2007-07-22
I want to make my system dual-boot.

Ubantu is already installed 
Details are as below -

    HDD size 40 GB
    swap - 1 GB
    Root partition 8 GB
    Home partition 8 GB
    Free space 23 GB

While installing XP, following partition info is shown on screen
  Partition C size 813 Mb (type - un-known)
  Partition E size 7366 Mb (type - unknown)
  Partition F size 7366 Mb (type unknown)
   UnPartitioned space 21GB

For installing XP i am selecting the unpartitioned space. However following error is thrown up
Maximum number of partitions already exist
Cannot create partition

Any help

pkj

---

### Post by nitro_n2o on 2007-07-22
Your r creating primary partitions which is wrong.. you should create logical partitions

---

### Post by ddrichardson on 2007-07-22
nitro_n20 is right - the maximum number of primary partitions on a drive is 4.

However as you see there are only 3 primaries created. For some reason that I've never worked out Windows almost always miscalculates the space when creating an install partition - so there are two things you can do:

1. Don't use quite all the space for the windows partition
2. Have a logical partition for Linux and one for windows. You can subdivide these into further extended partitions.

---

### Post by pkj on 2007-07-22
Will be grateful if you can further elaborate on it as to how to create these partitions. I already have ubantu up and running

pkj

---

### Post by ddrichardson on 2007-07-22
Well, conversion in a nause, so use synaptic to install gparted then create a fat32 partition on the unused space.

Your file table appears to have only 3 primary partitions so this should be possible. Once its created windows should be happy to format and install on that partition.

Also I should mention that when you install Windows you will lose grub from the MBR, and will need to [recover it]("http://www.sorgonet.com/linux/grubrestore/").

---

### Post by pkj on 2007-07-22
Thanks

Will take a while to do all this.

Will revert back if problem persists

pkj

---

