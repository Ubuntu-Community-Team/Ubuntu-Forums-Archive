---
title: "How are other volumes labeled?"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by Shack_ on 2007-03-03
I understand that to mount a drive you need to specify the device, like /dev/hda1, but why are these devices labeled like this? And what is the difference between hda1 and sda1? Is there such a thing as hdb1?

And am I right that the number at the end of each device name is referring to a partition?

It would be nice to have this explained to me.

---

### Post by tgalati4 on 2007-03-03
Upon boot, the kernel goes through a hardware detection routine and labels any devices that it thinks are disks as follows:

First IDE Master Disk /dev/hda
First IDE Slave Disk /dev/hdb

Second IDE Master Disk /dev/hdc
Second IDE Slave Disk /dev/hdd

First SCSI Disk /dev/sda
etc.

Partitions are given an incremental number.

The first partition on the first disk is typically /dev/hda1

Look in /boot/grub/device.map to see quick list of what devices were found.

Welcome to the community.

---

### Post by Quillz on 2007-03-03
HDA means you have a typical hard drive, where SDA means you have a newer Serial ATA hard drive.

---

