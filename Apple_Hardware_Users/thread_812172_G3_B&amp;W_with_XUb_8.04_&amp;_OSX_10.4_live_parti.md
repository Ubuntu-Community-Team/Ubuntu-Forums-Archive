---
title: "G3 B&amp;W with XUb 8.04 &amp; OSX 10.4:: live partitioning how to"
date: 2008-05-29
forum: Apple Hardware Users
---

### Post by Giamby986 on 2008-05-29
Hi guys,
after some good time with Xubuntu I need to install Mac OS X Tiger back again on my G3 B&W... without touching Xubuntu [only shrinking its partition, _no erasing_]... 
and that's where I've found some problems, having completely no experience on partitioning and multiple system on a single HD.

::doubts::

1. 
How can I make a good HFS+ partition for Mac OS with Xubuntu?
Should I use pmac-fdisk? or GParted? how... from the live cd?

2.
Can I make the partition from the Mac OS X installation CD with Disk Utility?
[although I know Disk Utility on Tiger won't do live partitioning...]

3.
How to part/install without mess with my Xubuntu partitions?

4.
How to make the double boot? [with linux as default os]


See, to make this [rather simple] story short::
I need to install Tiger without touching _anything_ about Xubuntu...

My main partition is /dev/hdc3 228.0 GiB with 206.7 free

[command~$ sudo pmac-fdisk /dev/hdc prints:]
The number of cylinders for this disk is set to 30401.
This is larger than 1024, and may cause problems with:
1) software that runs at boot time (e.g., LILO)
2) booting and partitioning software form other OSs
   (e.g., DOS FDISK, OS/2 FDISK)
Warning: invalid flag 0000 of partition table 4 will be corrected by w(rite)
[the -p option:]
Disk /dev/hdc: 255 heads, 63 sectors, 30401 cylinders
Units = cylinders of 16065 * 512 bytes

so... here I am, waiting for something interesting...

Thanks guys.

::Giamby::

---

