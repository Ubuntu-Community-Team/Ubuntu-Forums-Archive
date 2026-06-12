---
title: "GParted shows HD as unallocated"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by Nekiruhs on 2008-01-03
OK, BIG problem here. I just installed Ubuntu on my laptop. Everything works for the most part. Except now GParted shows my HD as unallocated space. All 149 GiB of it is unallocated. I know this not to be true as I can boot Ubuntu off of my HD as well as Windows XP and Dell MediaDirect (With an error I believe to be related to this issue). How do I fix this? It is really freaking me out! Screenshot attached.

---

### Post by dstew on 2008-01-03
Maybe gparted is not able to work with a disk that is mounted on the same system that it is running in. Try gparted from a LiveCD boot, when the hard disk is unmounted, and see if it looks different.

---

### Post by Nekiruhs on 2008-01-03
No, I've definitely been able to use GParted on a running disk before. The LiveCD does the same thing as well though.

---

### Post by Pogeymanz on 2008-01-03
It sounds like your partition table was blown up.

This happened to me when I tried to triple boot with PCLOS. Google for "Super grub disk", download it and boot with that. Use the "analyze" option and it will find your partitions and write them to your partition tables. Make sure to read about it first.

---

### Post by Nekiruhs on 2008-01-03
> **EmosSuck777 said:**
> It sounds like your partition table was blown up.

This happened to me when I tried to triple boot with PCLOS. Google for "Super grub disk", download it and boot with that. Use the "analyze" option and it will find your partitions and write them to your partition tables. Make sure to read about it first.
Hmm. GRUB didn't seem to like that. It threw Error 17 at me, I'm now typing this from my desktop.

---

### Post by Pogeymanz on 2008-01-03
Did SuperGRUBdisk restore the partitions to the right setup? How many partitions did you have before/after you installed Ubuntu? How many does gparted show now? Are they numbered correctly?

---

### Post by joshuanv28 on 2008-01-03
is the disk Mounted?? You cant create a partition right? Try unmounting it. Right click then unmount. I ran into a problem like this when i first set up my server box. maybe that is the problem

---

### Post by hotdoog on 2008-05-22
Any luck?

I have the same problem. I'm shuffling around partitions and moved my boot partion. Then I re-ordered the device naming (f) using (x) expert mode in fdisk. But then I was getting errors doing that that the device was busy. And I got confused and rebooted instead of moving the grub/mbr pointers.

Anyway, I'm currently using the super grub disk to boot into this. Which seems to work fine as a temporary measure. Not sure how to fix this though.

Why is gparted acting this way??? My currently supergrubcd booted (from HDD) OS is recognising all the partitions and mounting them and reading from them.

I may try getting a newer version of supergrub cd because I'm using an old version and the UI is confusing. If you are still having problems definately try [supergrubdisk]("http://www.supergrubdisk.org/") though it is confusing. I am currently using it to boot my somehow broken system.

If it is that the MBR is missing or something it would be nice if gparted were more intelligent and look at whatever fdisk looks at because its all there still!

---

