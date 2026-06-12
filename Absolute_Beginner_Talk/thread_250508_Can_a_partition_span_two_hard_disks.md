---
title: "Can a partition span two hard disks?"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by stig on 2006-09-04
I have a PC with an 80GB hard disk using Dapper. Also I have a spare 80GB hard disk, originally from this PC, which has only Windows 98 on it. I want to re-instal the older "Windows disk" as a secondary hard drive alongside the "Ubuntu disk" - and wipe Windows to allow me to use it as an extension to the current Ubuntu set-up, perhaps putting my Home directory on it.

The Ubuntu disk currently has the standard default partitioning done automatically during installation. I could devote the second disk to the Home folder but there is still a lot of free space on the first disk - is it possible to make a partiton for my Home folder that used all of the second disk and part of the first? Or is it impossible for partitions to span disks?

---

### Post by monktbd on 2006-09-04
What could be done easily is to mount your second disk as a subdirectory of your home, e.g. as /home/myuser/data.

this means that everything in your home folder is one disc one expect data and subfolders in the /home/myuser/data folder.

to span entire partitions over more than one disc you should read about raid and lvm (logical volume manager).

but i think that the first solution (mounting the second disk there where you want it) is the better option.

you could even make more than one partitin on your second harddisk and mount it to any sufolder of your home (e.g. to also have a/home/myuser/downloads on disc two).

---

### Post by stig on 2006-09-04
> **monktbd said:**
> What could be done easily is to mount your second disk as a subdirectory of your home, e.g. as /home/myuser/data.

Thanks for the idea - it sounds like a creative approach to the problem.

I'm not familiar with partitioning but I guess I would still have to set a partition on the second disk to wipe off the Windows and make it ready for Ubuntu. Would it just mean making the whole disk an ext3 partition?

---

### Post by monktbd on 2006-09-04
> **stig said:**
> I'm not familiar with partitioning but I guess I would still have to set a partition on the second disk to wipe off the Windows and make it ready for Ubuntu. Would it just mean making the whole disk an ext3 partition?

you have different options here:

if you never want to share that data easily with windows make it ext3 or ReiserFS or any proper linux FS you would like.

what you should consider is whether you want one big partition or a couple smaller ones to mount them at different locations.
it is adviseable anyway to have /home complelty on a different partition. makes a reinstall so much easier :).

so: if you want only one folder where you mount the new disk: you can make it all one big partition, probably ext3 is the best choice.
if you want to have more mount points for it choose smaller partitions and mount them wherever you want.

the disk utility in the systems menu will help you setting this up.

---

### Post by tageiru on 2006-09-04
> **stig said:**
> is it possible to make a partiton for my Home folder that used all of the second disk and part of the first? Or is it impossible for partitions to span disks?

Yes it is possible. LVM allows you to add disks and partitions into volume groups. You are free to create logical volumes on top of these pretty much any way you want, in this case creating a partition that spans two disks. 

This is however fairly complex, you need to have a bit of knowledge on Linux partitioning and LVM.

---

### Post by stig on 2006-09-04
When data is divided between two hard disks is there any difference in the speed at which it can be processed?

In other words, is the data that resides on the same disk as the operating system and applications handled faster than the data that is on the separate disk?

---

### Post by monktbd on 2006-09-04
no.

it only depends on the harddisk itself, its connection type and the filesystem on it. and of course where on the harddisk the wanted data is.
(e.g. ReiserFs is faster for small files, fat32 is slower overall,...)
advantage of linux filesystems is that they do not get fragmented so you dont need a defragmenter.

---

