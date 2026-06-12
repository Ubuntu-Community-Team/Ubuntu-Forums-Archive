---
title: "Hard drive problem"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by Brutus2006 on 2007-07-01
Im running Fiesty all was working fine, I log on today and a message comes up hard drive is full. Im thinking that is strange so I check. I know I have a 60 gig hard drive but when I check in System Monitor I only show 13.1 GB  which now is 100 % full. Confused here did I install Ubuntu wrong?
How can I resize partion is that the answer?

---

### Post by drowner on 2007-07-01
Are you dual booting? Tell us about the partitions

can you show us the output of:

sudo fdisk -l

---

### Post by Brutus2006 on 2007-07-01
Disk /dev/sda: 15.0 GB, 15020457984 bytes
255 heads, 63 sectors/track, 1826 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1744    14008648+  83  Linux
/dev/sda2            1745        1826      658665    5  Extended
/dev/sda5            1745        1826      658633+  82  Linux swap / Solaris

Disk /dev/sdb: 60.0 GB, 60040544256 bytes
255 heads, 63 sectors/track, 7299 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7112    57127108+  83  Linux
/dev/sdb2            7113        7299     1502077+   5  Extended
/dev/sdb5            7113        7299     1502046   82  Linux swap / Solaris

---

### Post by Brutus2006 on 2007-07-01
What I have is Fiessty on the 15 GB I thought it was on my other hard drive which is 60GB I have Ubuntu Studio 
I used my 15 GB with XP and it never filled up. I dont have much iin my 15 of any use no music or pictures I was surprised it filled up so fast ..Unistalling some programs I dont use might help I guess

---

