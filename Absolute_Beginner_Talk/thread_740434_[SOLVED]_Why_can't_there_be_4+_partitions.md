---
title: "[SOLVED] Why can't there be 4+ partitions?"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by slughappy1 on 2008-03-30
Why can't I have more than 4 partitions? I have Vista installed, and then I was going to install Ubuntu with a separate home partition but I can't have that many partitions. I have:
```
/dev/sda1 ntfs /media/sda1
/dev/sda2 ext2 /boot
/dev/sda3 swap
/dev/sda4 ext3 /
```
but then I also wanted /dev/sda5 ext3 /home. Do I have to have a swap? I have installed Ubuntu before and if I tell it to just take up the whole drive I get a sda1 and sda5.

---

### Post by saj0577 on 2008-03-30
You can only have 4 primary partitions but you can also have extended partitions i belive.(unlimited extended?)

Saj

---

### Post by slughappy1 on 2008-03-30
So then how would I do what I want?

---

### Post by saj0577 on 2008-03-30
Dont quote me on this but im fairly sure this is correct.

Primary partitons are bootable.
So you would want your vista and your ubuntu partitions as primary.
Then make your swap and home partition extended partitions i belive there called.

When using gparted and creating new partitions it should give you the option to choose what type of partition you want.



Saj

---

### Post by Eclipse. on 2008-03-30
You can have as many partitions as you want, just only 4 primary.I have 5 atm.

Home Partition
Gutsy 
Hardy
Gentoo
Xp

---

### Post by Penguin Power on 2008-03-30
You need to have any **Windows** installations on a primary partition or (I am pretty sure) they will not boot. You also need to have the** /boot **section of a GNU/LInux installation on a primary partition.

As has been said, you can still create an extended partition and have as many partitions as you need. **/var**, **/home** and so on are all happy on logical partitions without any issues.

---

### Post by slughappy1 on 2008-03-30
Ok thanks, that worked. I made sda2 /boot and sda3 / primary. I then I made sda5 swap and sda6 /home logical. And it let me, so thanks

---

### Post by smurphy_it on 2008-03-30
Sounds like you understand.  Perhaps this thread should be marked as "Solved".

---

### Post by saj0577 on 2008-03-30
No problem.

Please mark as solved via thread tools :)

Saj

---

