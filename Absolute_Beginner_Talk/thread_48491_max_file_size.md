---
title: "max file size ?"
date: 2005-07-12
forum: Absolute Beginner Talk
---

### Post by rollinator on 2005-07-12
Hello,
Does Anybody know what the actual file size limit of Linux (especially of Ubuntu) is?
I heard that there is a 2GB limit. Is this barrier still present?
bye,
Rolli

---

### Post by UbuWu on 2005-07-13
It depends on which filesystem you use. The default on Ubuntu is ext3, which has a maximum file size depending on your configuration of at least 16 gigabyte and max. 2 terabyte. Only the older windows filesystems, like fat16 and fat32 have a size limit of 4 gigabyte.

See also:
[http://en.wikipedia.org/wiki/Comparison_of_file_systems#Limits](http://en.wikipedia.org/wiki/Comparison_of_file_systems#Limits)

---

### Post by ubuntu_demon on 2005-07-13
[QUOTE=rollinator]Hello,
Does Anybody know what the actual file size limit of Linux (especially of Ubuntu) is?
I heard that there is a 2GB limit. Is this barrier still present?
bye,
Rolli[/QUOTE]

at least 16 GB if you are using ext3 (which is the default)
see : [http://www.suse.de/~aj/linux_lfs.html](http://www.suse.de/~aj/linux_lfs.html)
(Ubuntu is build on debian. LFS in is debian so it is in Ubuntu.)

---

### Post by rollinator on 2005-07-13
[QUOTE=UbuWu]It depends on which filesystem you use. The default on Ubuntu is ext3, which has a maximum file size depending on your configuration of at least 16 gigabyte and max. 2 terabyte. Only the older windows filesystems, like fat16 and fat32 have a size limit of 4 gigabyte.

Hello,
Thanks a lot but what means it depends on my configuration what kind of configuration please gimme some examples. When is the limit 16Gb and when is the limit 2terabyte?.
bye,
Rolli

---

### Post by ubuntu_demon on 2005-07-13
[QUOTE=rollinator][QUOTE=UbuWu]It depends on which filesystem you use. The default on Ubuntu is ext3, which has a maximum file size depending on your configuration of at least 16 gigabyte and max. 2 terabyte. Only the older windows filesystems, like fat16 and fat32 have a size limit of 4 gigabyte.

Hello,
Thanks a lot but what means it depends on my configuration what kind of configuration please gimme some examples. When is the limit 16Gb and when is the limit 2terabyte?.
bye,
Rolli[/QUOTE]
 depends on the blocksize. I don't have time to look what's an easy way of seeing the current blocksize.

Bu default blocksize depends on the size of the partition. When you are in need of big files you can set the blocksize yourself (using mkfs).

---

### Post by UbuWu on 2005-07-13
No idea, it depends on the block size, I don't know what block size Ubuntu uses.

This is what wikipedia says about it:
For filesystems that have variable allocation unit (block/cluster) sizes, a range of size are given, indicating the maximum volume sizes for the minimum and the maximum possible allocation unit sizes of the filesystem (e.g. 512 bytes and 128KiB for FAT — which is the cluster size range allowed by the on-disc data structures, although some Installable File System drivers and operating systems do not support cluster sizes larger than 32KiB).

Just curious: for what purpose are you going to use >16gb files?? Any plans?

---

### Post by RJARRRPCGP on 2005-07-13
FAT16 is the one with a 2 GB limit. That's the FAT file system used by DOS, Windows 3.1 and Windows 95 pre-OSR2.

---

### Post by marcovanbeek on 2005-08-13
The 2TB limit is a hardware addressing limit for all 32bit processors. You need to run a 64 bit processing system to use more than 2TB. Also the standard partition table appears to be 32 bit as well, so this needs to be changed to gpt, and we think (Monday's little job) that running fsck on bootup trashes the partition table. We are able to create, format and mount a 4.4TB partition (12 x 400GB on a 3ware 9000), but it doesn't survive a reboot. yet.

Regards,

Marco.

---

### Post by Lord Illidan on 2005-08-13
I don't think you will be using 16 gb files, except maybe in video!!

---

### Post by jeremy on 2005-08-13
If my memory serves me well, there is a 2GB limit on files burnt to a dvd.

---

