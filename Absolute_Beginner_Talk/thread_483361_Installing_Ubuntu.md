---
title: "Installing Ubuntu"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by jhawk43 on 2007-06-24
Here i go again. First, I want to install ubuntu on my external hard drive. I want to create a partition on that drive using Acronis Disk Director using ext3 file system prior to installing ubuntu. Will that work?
Then when i boot from the ubuntu Live CD will i be able to install into that recent created partition?
Last but not least, when I install ubuntu will I be able to load grub on that particular partition and not screw up my windows bootloader?
I have never worked with a Linux system so am rather ignorant of the total process. Any help would be appreciated.

---

### Post by overdrank on 2007-06-24
> **jhawk43 said:**
> Here i go again. First, I want to install ubuntu on my external hard drive. I want to create a partition on that drive using Acronis Disk Director using ext3 file system prior to installing ubuntu. Will that work?
Then when i boot from the ubuntu Live CD will i be able to install into that recent created partition?
Last but not least, when I install ubuntu will I be able to load grub on that particular partition and not screw up my windows bootloader?
I have never worked with a Linux system so am rather ignorant of the total process. Any help would be appreciated.

Hi you can create and install on a partition with the live cd without creating the partition first, Now as for installing the grub on the usb I have not done that so I cant say but I would assume that ubuntu would ask if you wanted installed there.

---

### Post by JayTee on 2007-06-24
You should be able to install GRUB to that drive but you'll need to make sure that that drive is set to be the first drive in your BIOS boot device priority. I wouldn't bother setting up an ext3 partition first. I'd just leave available space on that drive for a linux partition of the size you want for / and some additional space for a swap partition and let Ubuntu create the partitions for you.

---

