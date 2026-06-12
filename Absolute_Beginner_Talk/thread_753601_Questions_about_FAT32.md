---
title: "Questions about FAT32"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by gyzer on 2008-04-12
I was under the impression that a Linux operating system could be installed on a FAT32 partition, is that wrong?

I currently have two hard drives. A 80GB which is the one that I want to install Ubuntu on, and a 200GB hard drive that has all my movies, music, docs and all that stuff from windows which is a FAT32 partition right now. 

I thought that if I had both drives formatted to FAT32 then everything would be fine. Do I indeed have to have Ubuntu installed on a ext3 partition?

Should I then carve up my 80GB drive into two partitions? Like a 50GB one for Ubuntu in ext3, and the remaining in FAT32 for additional storage space?

---

### Post by lsutiger on 2008-04-12
That is correct. When I first installed Ubuntu, I was dual booting on a FAT32 drive.

---

### Post by gyzer on 2008-04-12
Well the problem is, when I try to install it on a FAT32 formatted drive with the "/" mount point, it says that it cannot install using that kind of file system.

Should I then just do like a 50GB partition in ext3 and the remaining amount on that hard drive in a FAT32 partition for storage?

---

### Post by JoshuaRL on 2008-04-12
I would suggest that, ext3 is just a better filesystem.  And with it, you won't have to worry about the disk becoming fragmented.

---

### Post by gyzer on 2008-04-12
Ok. Would a 50GB ext3 partition be more then big enough for Ubuntu?

---

### Post by JoshuaRL on 2008-04-12
Yep, should be.  But you'll want to use a 1 or 2 GB swap partition too.  That is like the page file in Windows and takes care of RAM overrun.

---

### Post by gyzer on 2008-04-12
Is the swap partition also an ext3 partition? How should it be mounted?

---

### Post by JoshuaRL on 2008-04-12
It will be one of the types of partitions you can make.  A Linux Swap partition.  In the manual install or Gparted it should let you make one of those.

---

### Post by PeterJS on 2008-04-12
Linux supports reading and writing FAT32 (as it does NTFS), but you can't use FAT32 for your root partition (or /home, if you have one) because FAT32 doesn't support file ownership or permissions.

---

### Post by gyzer on 2008-04-12
Thanks for the clarification PeterJS

---

