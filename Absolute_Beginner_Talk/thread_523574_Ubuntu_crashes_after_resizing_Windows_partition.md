---
title: "Ubuntu crashes after resizing Windows partition"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by infernus_crusher on 2007-08-12
This is a problem that has happened to me twice. Both happen when I resized Windows partition (and therefore Ubuntu as well).The software I used was Paragon Hard Disk Manager 8.0.

After resizing, Ubuntu will no longer boot. It comes into a GRUB screen (black bg and white text) asking for a manual fsck. Apparently some of the root files have been corrupted.

Is there a way to fix it without losing all my data in Ubuntu?

---

### Post by undertakingyou on 2007-08-12
I bet that it renamed the partitions.  So for example if ubuntu was on /dev/sda2 before maybe that partition was renamed to sda3.  You could use a live cd of gparted to look at the names and then edit the grub menu and fstab to reflect that.  To edit those you may have to use a live cd like knoppix.

---

### Post by ron999 on 2007-08-12
Hi
I don't think that it is the GRUB menu.lst that needs attention.

This is my opinion:-

The file /etc/fstab holds the locations of the linux and swap partitions. But it doesn't record them in format  /dev/hda1, instead it uses UUID numbers. So if the partitions have been moved during resizing then you will need to change the UUID number(s) in this file.
This is how to go about it.

Boot from the Ubuntu LiveCD. Then use Places > Computer and click on the hard drive icon to mount it.

Then type into the monitor **sudo nautilus** and navigate to the fstab file. It will be in file system > media > disk > etc. You will be able to see the stored UUID numbers.

Next find the actual correct UUID numbers by copying and pasting this into the monitor:-
 **ls -l /dev/disk/by-uuid**
You will be able to see the correct UUID numbers. Compare them with the ones in your fstab file.

If they need to be changed then use sudo nautilus to open up the fstab file again and edit it with the correct UUID numbers and save it.

Then reboot from the hard drive.
:cool:

---

