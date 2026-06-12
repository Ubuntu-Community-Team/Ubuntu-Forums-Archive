---
title: "partitioning problems"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by gupta_sumesh63 on 2007-08-18
Hi,
My partitions are as follows:

> /dev/sda1      ntfs    24.41GB
/dev/sda2      ext3   27.94GB
/dev/sda3     extended   22.18GB
/dev/sda6     linux swap   1.22 GB
/unallocated   unallocated   7.84 MB
/dev/sda5      fat32           20.95 GB

I wish to reduce /dev/sda5  to 10 GB. Combine the balance with unallocated and add it to /dev/sda2 so that I get a larger ubuntu partition.

Gparted is available on Ubuntu LiveCD.

But how to go about it?
Please help me someone.
Thanx.

---

### Post by src2206 on 2007-08-18
It will be easier if you use Gparted separately to alter the partition sizes.

You may use a Live USB version available here: [http://gparted.sourceforge.net/liveusb.php](http://gparted.sourceforge.net/liveusb.php)

or a Live CD version available here: [http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

---

### Post by gupta_sumesh63 on 2007-08-19
I have resized the Fat volume to 10 GB. I want to move the unallocated space next to ext3 partition so that I can resize it. 
My Gparted Live CD boots into Grub rather than shell.:confused:
What shoul be done.
Some advice on partitioning using Ubuntu Live CD will be appreciable as that is working fine.
Thanks

---

### Post by Arthur Archnix on 2007-08-19
> **gupta_sumesh63 said:**
> Hi,
I wish to reduce /dev/sda5  to 10 GB. Combine the balance with unallocated and add it to /dev/sda2 so that I get a larger ubuntu partition.
But how to go about it?
Please help me someone.
Thanx.

Not possible. 

/sda5 is part of an extended partition. There is no way to add that space to /sda2 which is a primary partition. You have to delete your extended partition, resize /dev/sda2, then recreate your extended partition.

---

### Post by gupta_sumesh63 on 2007-08-19
Can I use the Ubuntu Live CD to do all that? i.e delete extended partition and resize my ext3 volume and then create extended, swap and a small fat32 volume?:(

---

### Post by Arthur Archnix on 2007-08-19
Perhaps... but I'd use a gparted live cd.

You can get it [here]("http://gparted.sourceforge.net/livecd.php").

---

### Post by antoz on 2007-08-19
an other option would be to create an other ext3 partition to use as a separate  "home" that way you don't have to alter the existing Ubuntu partition.
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by Arthur Archnix on 2007-08-19
Gupta, I think the above poster might be right. I could be possible to format the spare space, and then  tell ubuntu to treat the partition as if it were part of the same partition.

---

