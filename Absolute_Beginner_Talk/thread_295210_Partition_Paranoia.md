---
title: "Partition Paranoia"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by freebee271 on 2006-11-07
Two quick questions. 
Will the live CD installer ask for: 
1) location to install Ubuntu 6.10.
2) Amount of space to allocate for Linux install.

I am afraid to partition my hd myself. It came from the factory with three (Fat32) partitions.
The notebook is an entry level Acer with 512ram - 40GB hd - XPsp2
It is partitioned as follows:

       Filesys       Size           Used         unused   Flag
hda1    fat32       3.91GB         2.92GB        1011.77m
hda2    fat32      16.43GB          ----          ----   boot iba
hda3    fat32      16.91           1.02GB        15.89
unalocated ---         ---         -----          ---

I would like to install Ubuntu on hda3 and use about 10GB will the installer allow me to set the parameters or will it choose some pre determined setup?

I have read several tutorials as well as many threads here and I can't seem to find the short answer.

Thanks in advance.

---

### Post by mattkirwan on 2006-11-07
The Live CD installer will let you custom partition your hard drive, be sure to select the right option when asked.

Also, of that 10gb you want to allocate, leave 1gb for 'swap'

---

### Post by Fully216 on 2006-11-07
The partitioning software has the same feel as Partition Magic, if you have ever used that software before.  It will allow you to delete, resize, and create partitions, so you should have no trouble.  It is very easy/intuitive with both a graphical representation of your drive space and a numerical one as well.

On a side note, you should have no trouble reading/writing to your other drives as well because they are FAT32.  Writing to NTFS is still experimental.

EDIT: You need as much swap space as you have RAM.

---

### Post by freebee271 on 2006-11-07
Wow that was fast...Thanks.

If I re-partition / resize my hd3 will I lose the data that is already on it?

---

### Post by bsussman on 2006-11-07
The term re-partition can describe cases where data is intentionally destroyed and cases where it is not.  So the answer this part of your question is yes and no.  I only use the term to describe cases where all data is destroyed.

You **can** resize without losing data.

But if you do lose something, you can restore from the backup that you wouldn't resize without doing first... :)

---

### Post by freebee271 on 2006-11-07
> But if you do lose something, you can restore from the backup that you wouldn't resize without doing first... 


I'm sharp like that;) Thanks!

Everything worked well from the live CD, I'm excited to get started using a real install.
I just want to understand all that I can prior to the install.

---

### Post by bsussman on 2006-11-07
1. Go slowly
2. Take notes
3. ubuntu doesn't do big things without telling you and requiring your acknowledgement.  Don't say yes unless you understand.

ubuntu really is not that hard, though 6.10 is proving to be a little more challenging. 6.06 is solid.

Good luck - :)

---

