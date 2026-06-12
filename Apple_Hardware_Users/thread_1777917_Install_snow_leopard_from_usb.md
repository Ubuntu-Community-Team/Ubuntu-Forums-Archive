---
title: "Install snow leopard from usb"
date: 2011-06-08
forum: Apple Hardware Users
---

### Post by whooper90 on 2011-06-08
Hey..
Having wiped all of my HDD and installed ubuntu (on macbook), I now want to install snow leopard again.
I've got a DMG that I made from my install DVD, and want to create a bootable USB to install from (because of no optical drive)..

How do I do that from ubuntu? :)

---

### Post by paulinchen on 2011-06-08
Maybe you should give this a try ...

[https://help.ubuntu.com/community/ManageDiscImages](https://help.ubuntu.com/community/ManageDiscImages)

Once you have an iso, I think you should be able to create a readable pendrive. Format it as hfsplus and copy-paste the mounted Image.
Honestly, in my case I always got an error trying to create an Image via DMG2IMG, neither worked it  with Acetoneiso. But maybe it works for you. 
I also found another possible solution, but I didn't tried it, cause I luckily still have my osx-partition ...

[http://ubuntuforums.org/showthread.php?t=135913](http://ubuntuforums.org/showthread.php?t=135913)

---

### Post by dubmartian on 2011-06-09
same story here with dmg to iso using ubuntu; limited effort, limited success. i can add - before formatting device to hfs, make sure partition table is gpt. both gparted and disk utility can set tables.

---

### Post by srs5694 on 2011-06-09
> **dubmartian said:**
> before formatting device to hfs, make sure partition table is gpt. both gparted and disk utility can set tables.

Be careful! If the goal is to create a dual-boot system, using GParted or Disk Utility to convert from MBR to GPT will be destructive -- they'll both wipe out all the MBR partitions! The job can be done non-destructively with GPT fdisk (gdisk), though.

This may be entirely moot, though; it's possible that the Ubuntu installation uses the disk in GPT form rather than in MBR form.

One other issue is that OS X tends to be a bit picky about its installation partitions; it likes to see 128 MiB or so of unallocated space after any partition to which it installs, so you should be sure to create the partition such that it's got that space. (If you use Apple's Disk Utility to create the partition, this shouldn't be a problem; it'll set it up the way it likes it.)

---

### Post by dubmartian on 2011-06-09
good points. i should have mentioned making partition table gpt with Ubuntu applies only to the usb device used to install Mac OS. i assume once running Mac OS installer, Macs disk utility would be used to create custom partition for dual boot.

---

