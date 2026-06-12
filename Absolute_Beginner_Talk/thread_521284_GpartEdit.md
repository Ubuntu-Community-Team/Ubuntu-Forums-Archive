---
title: "GpartEdit"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by ben22 on 2007-08-09
hello,

when starting the GpartEdit is see the following for the 320 GB drive


Partition                          Filesystem           Size
unallocated                     unallocated          296,83 GB
/dev/sda2 extended       extended             1,26 GB
   /dev/sda5                    linux/swap            1,26 GB

- What does linux swap stand for?
- how can I partition the whole drive to install Ubuntu, some space I may want to use to later instlal windwos on another partition?

---

### Post by splintercellguy on 2007-08-09
Linux swap is basically the paging partition that Ubuntu will use. My understanding is that Windows wants to be the first partition, so you could create at the beginning NTFS, and leave the rest blank. Let the installer partition for you and you should be good.

---

### Post by LaRoza on 2007-08-09
> **ben22 said:**
> hello,

when starting the GpartEdit is see the following for the 320 GB drive


Partition                          Filesystem           Size
unallocated                     unallocated          296,83 GB
/dev/sda2 extended       extended             1,26 GB
   /dev/sda5                    linux/swap            1,26 GB

- What does linux swap stand for?
- how can I partition the whole drive to install Ubuntu, some space I may want to use to later instlal windwos on another partition?

Do you mean GParted?

swap is your swap file, it should be about 512 MB big, but most of the time it is larger.

If you don't want to preserver anything on the drive, you can make three or four new partitions.

I would have:

/dev/sda1   ntfs    ~20 GB
/dev/sda2   ext3   ~20 GB
/dev/sda3   linux-swap  512 MB
/dev/sda4   extended   (the rest of the drive)


In the extended partition, you can make logical drives to share data with Windows and Linux. It will also keep data seperate from the OS.

---

### Post by dptxp on 2007-08-09
SWAP is used as RAM, for a hard disk of the size you have, 2 GB SWAP is not a luxury. It is useful when you have lot of stuff ( as multiple image editing) on RAM, you do not run out of memory.

---

### Post by LaRoza on 2007-08-09
> **dptxp said:**
> SWAP is used as RAM, for a hard disk of the size you have, 2 GB SWAP is not a luxury. It is useful when you have lot of stuff ( as multiple image editing) on RAM, you do not run out of memory.

Most people will need less than they think. People have used 128 MB and saw no difference from when they were using 2 gigs. 

Big swap partitions are not much of an issue when you have a large drive, so having a larger swap could be benificial if you anticipate such memory intensive activities.

To say swap is used as RAM is slightly misleading. Although it is true data in RAM will be written to swap so RAM can be used for something else, to use the data that was written to swap, it will have to be loaded into RAM again. Hard disk access is much slower than RAM access, so if are constantly using swap, it might be time to get more RAM.

---

### Post by dptxp on 2007-08-09
> **LaRoza said:**
> Most people will need less than they think. People have used 128 MB and saw no difference from when they were using 2 gigs. 

Big swap partitions are not much of an issue when you have a large drive, so having a larger swap could be benificial if you anticipate such memory intensive activities.

To say swap is used as RAM is slightly misleading. Although it is true data in RAM will be written to swap so RAM can be used for something else, to use the data that was written to swap, it will have to be loaded into RAM again. Hard disk access is much slower than RAM access, so if are constantly using swap, it might be time to get more RAM.

Obviously SWAP is much slower than RAM and if one does RAM intensive job more frequently, SWAP is not the solution. But if memory requirements are large only occasionally, SWAP comes to rescue.

An additional GB for SWAP on large hard disks  hardly eats into disk space. Increasing SWAP later can be a pain.

Normally if the RAM is large, or even moderate at 512 MB, small SWAP is OK. It is a matter of personal choice. I typically put it at end of HDD, 1.5 GB even on 60 GB HDD. And forget about it.

---

