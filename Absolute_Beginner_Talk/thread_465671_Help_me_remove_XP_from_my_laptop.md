---
title: "Help me remove XP from my laptop"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by ski309 on 2007-06-05
My XP bugged out on my Dell E1405, and I think that gives enough reason to pull out the partition and make the only partition Ubuntu.  Can anyone help me out with this?  I'd prefer not to reinstall Ubuntu, I have it set up the way I like and there's already stuff on it. I figure I can use gparted to remove the windows partition, copy the linux partition to the start of the drive, remove the original linux partition, and then resize the new linux partition to fit the entire hard drive.  Is this feasible?  Any pitfalls I should worry about, including making sure GRUB works?

Here's a paste of my 'sudo fdisk -l':

```
Disk /dev/sda: 58.5 GB, 58506416640 bytes
255 heads, 63 sectors/track, 7113 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        5790    46468012+   7  HPFS/NTFS
/dev/sda3            5791        7055    10161112+  83  Linux
/dev/sda4            7056        7113      465885    5  Extended
/dev/sda5            7056        7113      465853+  82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241    7  HPFS/NTFS

```
I don't know what the Dell Utility partition is.  I'd like to get rid of it too and have only my Linux partition and my swap partition but I'm worried that my laptop needs that partition for some reason.

---

### Post by southernman on 2007-06-05
The first thing I would do is run a backup to cd/dev. Google for psychocat, he is a member/moderator/admin here, with a lot of good howto's. Look for his howto on backing up.

Once you've done this, install Gparted via apt-get (command line) or Synaptic Package Manager.

Gparted will enable you to delete those windows partitions, which will give you room to then resize your ubuntu partitions.

One better, if your willing and trust in the backup you have or will make... just reformat the whole drive and then run your backup on it.

I know it's vague, but it will get you heading in a good direction for what you want to do.

Your dell partiton is assuredly a system restore partition. You'll be safe removing it since you won't be needing windows any longer.

---

