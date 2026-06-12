---
title: "5 Partition Dual Boot"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by falciron on 2007-03-02
I just _successfully_ downloaded a copy of Edgy Eft today and started the installation. I've gotten to step 5 without many problems. Here's my problem here, though:

74.53 GB usable on my hard drive.

4.43 GB partitioned by Windows XP as a recovery (D) drive.
30.00 GB partitioned for Windows XP as a main (C) drive.
1.00 GB partitioned for my linux-swap file. (512 MB RAM) Selected as a Primary Partition.
Here's where the problem lies. I need to create a 10 GB partition for my installation and use the rest for the fifth extended and logical partition (Other. Forget what this is called.).

It seems that Ubuntu will only allow four partitions. Are there any solutions and/or is my setup  optimal? Any help would be appreciated.

---

### Post by o_fortuna on 2007-03-03
At my count, you have everything you need: swap and root (the 10 GB).

However, if you do need more space, just create one logical (extended) partition, instead of the 10 GB partition. Then, create two partitions inside the extended partition to use for whatever else you need (maybe the /home directory?)

---

### Post by Amenemhet on 2007-03-03
You may only have 4 primary partitions. If you want more partitions you need to make one of them an extended partition, then create logical partitions in/on it. My suggestion would be to have as you do, a Windoze primary (for boot, os, updates etc) and a  second for data. Then either an extended with all the linux needed partitions or one more ( the 3rd primary) for linux root and then an extended with the swap and data partitions on that.

---

### Post by falciron on 2007-03-03
Thanks for the help. My book of _Ubuntu Unleashed_ didn't cover what the setup should be in the case of a backup partition being there.

---

### Post by falciron on 2007-03-03
OK. I'm still a bit stuck on step 5. I've set this up on my partition table:

74.53GB Usable on Hard Drive
----------------------------------------------------
4.43GB fat32 Recovery Windows (D) drive.
25.00GB ntfs Windows main (C) drive.
20.00GB ext3 primary for Linux Installation /dev/hda3
25.10GB extended
----->1GB linux-swap logical for swap file
----->24.10GB ? logical for files common to Windows and Linux

What should my filesystem type be on that last partition? Also, after this is done, what should I do on the next screen?

I see:
Mount Point/Size/Partition/Reformat

hda1/25GB/Partition 1 Disc/No
hda2/4GB/Partition 2 Disc/No
swap/1020GB/Partition 5 Disc/Yes
/ /20GB/Partition 3 Disc/Yes
 / / / (No choices/words at all, but the placeholders are still there. This is with setting the 24.10GB ? logical as a fat32.)

What should I do to get it to recognize that last partition?

---

