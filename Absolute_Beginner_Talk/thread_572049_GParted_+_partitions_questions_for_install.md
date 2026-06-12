---
title: "GParted + partitions questions for install"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by Hatfield on 2007-10-10
I have a thread over in Apple Intel forum that's not getting much traffic and I need answers quick since I'm right in the middle of partitioning.  Hoping to get it all installed before bed.

I'm using Gparted LiveCD to create a 10GB partition for Ubuntu at the end of my 160GB drive in my Macbook(already Boot Camped with Vista; intend to use EasyBCD to boot Ubuntu)
.
GParted sees:
/dev/sda1 ! <Green>Fat32 200MiB(size) boot(flags)
/dev/sda2 <purple>hfs+ 96GiB(size) 34.10Gib(used) 61.90GiB(unused)
unallocated <"darkpurple"> unallocated 128MiB(size)
/dev/sda3 <teal>ntfs 52.73Gib(size) 11.39Gib(used) 41.34GiB(unused)

I've resized the last partition (/dev/sda3) to 43732MiB(new size) and Free Space Following to 10264MiB.

Do I need to format the new free space to ext3 before I exit out of GParted?  And do I need to create a smaller swap partition now?

I'm really confused with the install process.

---

### Post by Paqman on 2007-10-10
> **Hatfield said:**
> 
Do I need to format the new free space to ext3 before I exit out of GParted?  


You got it.

> 
And do I need to create a smaller swap partition now?


Yep, very small though. Twice the size of your RAM is plenty.

---

### Post by Hatfield on 2007-10-10
So I again resize the new 10GB partition to 6GB so I'd have another partition of 4GB?  Should the new 4GB partition be before or after the 6GB?

Or should I just leave the 10GB alone and choose "Use the largest continuous free space" when I install the Ubuntu LiveCD?

---

### Post by conehead77 on 2007-10-10
> **Hatfield said:**
> Or should I just leave the 10GB alone and choose "Use the largest continuous free space" when I install the Ubuntu LiveCD?

this should work. i remember doing this at the comp of my GFs brother.

---

