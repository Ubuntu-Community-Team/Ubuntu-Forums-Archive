---
title: "Adding volume in GRUB - forget how to do it."
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by emarkay on 2006-11-22
I originally had the system mount all my HDU volumes, and then removed all but one from GRUB.  I now want to be able to access (for example) my volume of MP3's, which is (for example) on hard disk 2, volume "E" which is "dev/hda5" a fat32 vfat volume.

The access path is (obviously) "none" and it can not be "enabled" from Disks Manager.  

This is what I have in GRUB:

# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

What do I have to add to make hda5 accessible in Ubuntu - either all-the-time or just temporarily from Disks Manager.

THANKS!

---

### Post by taurus on 2006-11-22
If you want to access your harddrive in Ubuntu, you are supposed to modify /etc/fstab NOT /boot/grub/menu.lst!!!

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

