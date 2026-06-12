---
title: "dual boot of ubuntu and mac os tiger?"
date: 2009-03-21
forum: Apple Hardware Users
---

### Post by bigfefan on 2009-03-21
i've got a ppc powermac with an 80 gb hard drive and I want a dual boot of mac os 10.4.11 tiger and ubuntu hardy. how do I do it? (I want 40 gb for mac os and 40 gb for hardy).

---

### Post by bigfefan on 2009-03-21
...anyone?

---

### Post by tiresia on 2009-03-21
[http://ubuntuforums.org/showthread.php?t=1026342&highlight=dual+boot+mac+os](http://ubuntuforums.org/showthread.php?t=1026342&highlight=dual+boot+mac+os)

---

### Post by paul_mcl on 2009-03-23
> **bigfefan said:**
> i've got a ppc powermac with an 80 gb hard drive and I want a dual boot of mac os 10.4.11 tiger and ubuntu hardy. how do I do it? (I want 40 gb for mac os and 40 gb for hardy).

1. Use Ubuntu install CD or some live cd (like Finnix, [http://www.finnix.org](http://www.finnix.org)) to partition your hard drive (my personal favorite is mac-fdisk, but you may want to use some GUI tool for that).
2. Partition it, so /dev/hda1 is Apple Partition Map, /dev/hda2 is Apple Bootstrap (approx. 1 Mb is enough), /dev/hda3 (ext2) and /dev/hda4 (ext3) for linux, /dev/hda5 (HFS+) for mac os x.
3. Install linux.
4. Install Mac OS X.

---

### Post by bigfefan on 2009-03-23
thankeeeeeee everybody!

---

### Post by mkvnmtr on 2009-03-23
The method I use is to put the mac disk in and use the disk utility on the disk to form a partition for the mac os. I leave unformated the space I want to use for Ubuntu. Then I install the Mac os. Then I use the Ubuntu disk to install Ubuntu in the free space. For a first time install it is probably best if you don't try to make the partitions. Just let the disk install in the largest free space and it will form the partitions you need. Later when you know more about what you want lyou can change it.

---

### Post by bigfefan on 2009-03-25
> **mkvnmtr said:**
> The method I use is to put the mac disk in and use the disk utility on the disk to form a partition for the mac os. I leave unformated the space I want to use for Ubuntu. Then I install the Mac os. Then I use the Ubuntu disk to install Ubuntu in the free space. For a first time install it is probably best if you don't try to make the partitions. Just let the disk install in the largest free space and it will form the partitions you need. Later when you know more about what you want lyou can change it.

i tried that approach. at one point between disk optimizations, the mac os footprint exceeded its alloted disk space and I was unable to use mac os, so i had to reboot with the mac os install disk and reformat the drive and give one partition the entire drive. I'll boot within Q instead.

about that, It says in q that i have a bios date error and so ubuntu wouldn't boot in my q emulator... i had luck with a cracked version of windows 2000 sp4, though...

---

