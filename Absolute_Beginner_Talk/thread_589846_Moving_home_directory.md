---
title: "Moving /home directory"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by Netor on 2007-10-24
Is there a way to change the location of the /home directory other than creating a new partition and loading it at boot?
The reason is that the HD is almost fill and partitioned already, repartitioning it will make me loose massive data. 
The partition where i want the home directory to reside is my data partition (fat32) which is shared by xp and ubuntu. since it has already data on it I do not want to touch it, at most it would be ok to create a directory inside it.
I had a few ideas on what to do but I want to see if they are possible.

1) Make a symbolic link (ln -s) to another directory in another partition (/media/sda#/folder/home/)
I dont believe this would work but have not tried yet, I need confirmation that this is or is not the way to go.
2) Mount in fstab the directory (mount /media/sda#/folder/home/ /home) but since the partition is already mounting as /media/sda#/ this would conflict wouldnt it?

Are these 2 options at all possible or is the only way to separate home from OS is to create a new partition?
Thanks

---

### Post by danm-koder on 2007-10-24
AFAIK there's no way of placing your /home directory on a FAT32 partition, but I might be mistaken...

---

### Post by Netor on 2007-10-24
> **danm-koder said:**
> AFAIK there's no way of placing your /home directory on a FAT32 partition, but I might be mistaken...

Ok thanks, What if it where some other filesystem type. whether NTFS, Ext3 or 2, could those options work or not?

---

