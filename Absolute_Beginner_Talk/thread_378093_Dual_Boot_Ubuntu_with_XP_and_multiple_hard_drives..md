---
title: "Dual Boot Ubuntu with XP and multiple hard drives."
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by TheBoogieman on 2007-03-06
I am trying to get Ubuntu running on a system that I am using. I have an existing copy of XP on one hard drive at the moment, but I also have a second, empty, hard drive (250GB).
I would like to set up the second hard drive so that I can use it to dual boot Ubuntu and partition it so there is enough room for all the system files, programs, and data.
The hard drive also has to have a partition of about 120GB that is set aside to back up other machines on my home network.

Could someone please point me in the right direction to getting this set up, I am a complete newbie to linux so any help would be appriciated.

---

### Post by confused57 on 2007-03-06
This thread explains one option:
[http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

---

### Post by jjf on 2007-03-06
I've set up a couple dual-boot configurations now and have always found it straightforward.  Just follow the instructions on the Ubuntu CD.  Here's what I'd recommend:

Leave the Windows HD alone.
Format the 250 GB HD this way:

/ = 40 GB 
/home = 60 GB
swap = 1 GB
/backup = 149 GB  (use FAT32 so Windows partitions / machines can read and write to it)

---

