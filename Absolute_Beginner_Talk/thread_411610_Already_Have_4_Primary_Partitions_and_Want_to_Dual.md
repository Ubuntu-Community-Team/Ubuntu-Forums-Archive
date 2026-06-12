---
title: "Already Have 4 Primary Partitions and Want to DualBoot"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by Neo-genesis on 2007-04-17
So I have been trying hard to figure out how I can get Ubuntu installed on my computer with XP still intact.  Almost every single guide on dual booting works off of the premise that my hard drive only has one partition, but mine came with four already.  I have two NTFS partitions, a FAT16 and a FAT 32 partition.  I want to install Ubuntu on the second NTFS partition and then create a second partition within that for the Swap partition.  What I really need to know is

A) Can I do this?

B) How do I do it?

I figured that I need to format the partition, but I don't know what type to make it or how I can create the Swap  partition from there.  Thank you for reading this far and hopefully responding.

---

### Post by Bachstelze on 2007-04-17
You need to delete that partition and create a new extended partition instead. Then you can create as many logical partitions you want within the extended one.

---

### Post by Neo-genesis on 2007-04-17
Wow, I didn't know you could delete partitions.  That worked perfectly and I now have Ubuntu fully installed on my computer alongside windows.  Thanks!

---

