---
title: "Mount partitions help."
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by IsleOf on 2007-05-20
Trying to mount the partitions. This is what i get view the partition table.

> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sda1 1 4055 32571756 7 HPFS/NTFS
/dev/sda2 4056 12511 67922820 f W95 Ext'd (LBA)
/dev/sda3 * 12512 30401 143701425 83 Linux
/dev/sda5 4056 12133 64886503+ 7 HPFS/NTFS
/dev/sda6 12134 12511 3036253+ 82 Linux swap / Solaris

Disk /dev/sdb: 514 MB, 514981888 bytes
173 heads, 57 sectors/track, 102 cylinders
Units = cylinders of 9861 * 512 = 5048832 bytes

My hard drive was allready partitioned before linux into C and D drives. Why is there 5 partitions now. I thought Linux has a linux and a swap partition. Whats the extra partition? Does this make sense?

Sorry for a new thread. My last one wasnt getting any more views

---

### Post by ajmorris on 2007-05-20
> **IsleOf said:**
> Trying to mount the partitions. This is what i get view the partition table.



My hard drive was allready partitioned before linux into C and D drives. Why is there 5 partitions now. I thought Linux has a linux and a swap partition. Whats the extra partition? Does this make sense?

Sorry for a new thread. My last one wasnt getting any more views

the "W95 Ext'd (LBA)" is the 'extended' partition. It displays as W95 Ext'd (LBA) not extended, because this is the most common form and is recognised by most os's.

so.... What you have here is a Primary partition for the root directory /
and an Extended partition containing the swap partition.

This often occurs with 'automatic partitioning' and is really nothing to be concerned over. The reason is that current computers only support a total of 4 primary partitions so in order to get around this limitation, extended partitions are created. This allows more that 4 partitions to exist because the extended partition exists as a primary partition, but contains other partitions inside it.

You can safely remove the extended partition and recreate the swap partition as a primary partition by booting into the ubuntu live disk. You will need to update your /etc/fstab file after doing this.

(you'll notice the 'end' bocks are the same for the partition labelled linux swap and the Ext'd (LBA))

---

### Post by IsleOf on 2007-05-20
Cheers.

So SDA1 and SDA 5 are the windows partitions. To get access to thes i need to mount them. What the best guide to do this

---

### Post by taurus on 2007-05-20
[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by IsleOf on 2007-05-20
Thanks again. will give it a go

---

### Post by ajmorris on 2007-05-20
> **IsleOf said:**
> Cheers.

So SDA1 and SDA 5 are the windows partitions. To get access to thes i need to mount them. What the best guide to do this

Hang on, if you're going to remove the extended partition, before removing the extended partition, can you please post a screenshot of Start Menu >> System Tools >> Partition editor

I just want to make sure the swap file is in the extended not the main partition, also please not, most people have this extended partition anyway, and you do not need to remove it.

I don't know where a guide for mounting is off the top of my head, but

if you type in a terminal
```
sudo mount /dev/sda1
``` and ```
sudo mount /dev/sda5
``` that will mount them. and to mount them automatically on start up
add these to /etc/fstab: 

/dev/sda1       /media/sda1   ntfs auto 0       0
/dev/sda5       /media/sda5    ntfs auto 0      0

---

### Post by IsleOf on 2007-05-20
I dont want to remove it. I was just wondering why i had 5 partitions.

I just want access to files in my D drive.

---

