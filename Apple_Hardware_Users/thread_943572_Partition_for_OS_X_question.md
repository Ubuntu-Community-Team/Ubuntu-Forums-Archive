---
title: "Partition for OS X question"
date: 2008-10-10
forum: Apple Hardware Users
---

### Post by somethingkindawierd on 2008-10-10
I have a MacBook currently running Ubuntu. I need to put OS X on it for a project and want to simply add a new partition and install OS X on it without needing to reformat the entire drive.

I added a new partition using gparted, used Apple's disk utility to format the new partition, and upon starting to install OS X it says I must reformat the drive so it has a "guid partition scheme." Is there any way to do this without reformatting the entire drive? Or, is there any way to do this such that I can restore my Ubunut partition without needing to reinstall everything?

Thanks!

---

### Post by cyberdork33 on 2008-10-10
> **somethingkindawierd said:**
> upon starting to install OS X it says I must reformat the drive so it has a "guid partition scheme." Is there any way to do this without reformatting the entire drive?
Nope. When you installed Ubuntu only, you converted the drive to a typical MBR partition scheme. OSX will only install to a GUID Partition Scheme (with a GPT). What you CAN do is install OSX to an external device, then you can create and image of that install and restore it to your internal hard drive with the MBR partition scheme. OS X will boot from non-GPT disks, it just won't install to one.

Your other option would be to find a way to backup your Ubuntu partition and then restore it after reinstalling OSX (and wiping the drive).

---

