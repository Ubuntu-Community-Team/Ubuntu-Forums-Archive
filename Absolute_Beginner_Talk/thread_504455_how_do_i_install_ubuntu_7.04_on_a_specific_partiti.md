---
title: "how do i install ubuntu 7.04 on a specific partition?"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by rustix on 2007-07-19
i want to make a fresh installation of ubuntu alongside my present Windows XP (dual boot) and i need some help.. at the moment i've got 2 NTFS partitions, 2 FAT32 partitions, 1 linux ext3 partition and a (1GB) linux swap partition.. i want to install Ubuntu 7.04 on the linux ext3 partition... how do i do this??

it would be a great help if someone could a very detailed set of instructions...

**P.S. - **the linux swap partition is shown as a logical partition and the ext3 partition is primary partition. i used PowerQuest PartitionMagic 8.0 to create the partitions...

---

### Post by Zzl1xndd on 2007-07-19
> **rustix said:**
> i want to make a fresh installation of ubuntu alongside my present Windows XP (dual boot) and i need some help.. at the moment i've got 2 NTFS partitions, 2 FAT32 partitions, 1 linux ext3 partition and a (1GB) linux swap partition.. i want to install Ubuntu 7.04 on the linux ext3 partition... how do i do this??

it would be a great help if someone could a very detailed set of instructions...

**P.S. - **the linux swap partition is shown as a logical partition and the ext3 partition is primary partition. i used PowerQuest PartitionMagic 8.0 to create the partitions...

Should be easy just go threw the set up process and select that drive as the one to install on.

---

### Post by rustix on 2007-07-19
from where do you select the partition you want to install it on??

---

### Post by mikewhatever on 2007-07-19
Look at the pictures of the following guide [http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)
Since you've already created your partitions, skip the partitioning stage and mount the ext3 as / and the swap as swap. I think you'll need to format the root (/).

---

### Post by rustix on 2007-07-19
> **mikewhatever said:**
> Look at the pictures of the following guide [http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)
Since you've already created your partitions, skip the partitioning stage and mount the ext3 as / and the swap as swap. I think you'll need to format the root (/).

thanks... :)

---

