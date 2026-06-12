---
title: "Sharing a partition of files"
date: 2011-08-01
forum: Apple Hardware Users
---

### Post by megabenman on 2011-08-01
Hey everyone.  I am running a triple boot of Snow Leopard, Win7, and 11.04.  I tend to share files a lot between the partitions and I want to know if it would be easier just to create a fourth FAT32 for them to access.  I am fairly certain this would work, but would it be slower than just having them access their own partition?  Would I be able to set time machine to backup these other partition?

Also, this would require me shrinking the partitions, so what is the minimum amount of free space each partition should get?  15%?

---

### Post by nazgul42 on 2011-08-01
I've had to deal with a similar situation, except it was an external hard drive, not a partition. I found that a NTFS file system works pretty well. Ubuntu and Windows have native support for NTFS, but you need to install something like NTFS-3G or Paragon on Mac to access NTFS. NTFS-3G is free and works perfectly on Snow Leopard, but it does not work at all on Lion. Paragon costs $20, but it works on Lion if you are going to upgrade.

The minimum amount of free space depends on how big your hard drive is and what you want to use each partition for. 
Also, I don't think this would be any slower than accessing their own partition.

---

### Post by blane2 on 2011-08-01
> **megabenman said:**
> Hey everyone.  I am running a triple boot of Snow Leopard, Win7, and 11.04.  I tend to share files a lot between the partitions and I want to know if it would be easier just to create a fourth FAT32 for them to access.  I am fairly certain this would work, but would it be slower than just having them access their own partition?  Would I be able to set time machine to backup these other partition?

Also, this would require me shrinking the partitions, so what is the minimum amount of free space each partition should get?  15%?

They can all read and write to fat32 format. Time machine should back it up if you set it up to do that partition in the preferences.
The rest is your choice and desire.

---

