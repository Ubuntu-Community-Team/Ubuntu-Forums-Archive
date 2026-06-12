---
title: "Grub error 17. Ouch....... help please!"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by vto80 on 2007-02-11
Hello world (again)!

I'm in trouble. After spending considerable time and bandwidth (it's not free around here thanks to Deutche Telekom) on setting up egdy eft just the way i like it, i find myself unable to boot both xp and ubuntu. 
Not sure what happened myself... The partition table was like this:
hda1 - xp (ntfs)
hda5 - linux swap
hda6 - storage space (ext2 accessible from both xp and ubuntu)
hda7 - ubuntu (ext3)

Then i decided to convert hda6 to ntfs, to save the hassle of checking the ext2 volume on each ubuntu boot. I heard there is a ntfs rw driver, ntfs-3g, that works for both reading and writing to ntfs partitions, so i wanted to try that.

In xp, i deleted the ext2 partition, but doing so deleted the linux swap also (?????). I couldn't format the ex ext2 partition, so i rebooted the machine, and found myself with grub's extremely verbose 'Error 17'.
Using the Live CD, i re-created the deleted linux swap partition (do i need to format it too, and how do i do it?). But this time, the partition table (from fdisk) looks like this:
hda1 - xp
hda5 - ubuntu
hda6 - fat16
hda7 - swap

SO, i guessed that's why grub won't start. Proceeded to mount /dev/hda5 and edit grub's menu.lst, replacing (0, hd6) with (0, hd4) and /dev/hda7 with /dev/hda5. And then doing the same in fstab, removing the UUID entries (what are they for anyway?) with the correct /dev/hda addresses. 

But i find myself staring at Error 17 once again :( 

The interesting thing is, in xp, disk manager showed a different setup:
xp partition
extended
   linux swap
   ubuntu
   storage space

vto.

---

### Post by daou on 2007-02-11
When you boot into Grub, press 'e' to edit the boot configuration of Ubuntu. Try all different possibilities (0, hda5), (0, hda4) etc. until you get the right one. It seems like your Ubuntu is on an extended partition, and this usually increments partition numbers.

---

### Post by vto80 on 2007-02-11
That's not an option. Grub doesn't load. It's probably looking for menu.lst in the wrong place. If that's so, i guess i should somehow edit whatever Grub wrote to the mbr. But how do i do that?

vto.

---

### Post by bulldog on 2007-02-11
The best thing you can do is boot from the live cd.
Then ```
sudo fdisk -l
``` to see how Ubuntu thinks about your partition names.
If you figured out how your menu.lst should look like,mount your existing ubuntu partition and edit the menu.lst.
Don't forget to change the fstab with the new information as well.

---

### Post by daou on 2007-02-11
If you can't even get to Grub, then the best thing to do is to reinstall Grub from the LiveCD. [How to reinstall Grub.]("http://www.ubuntuforums.org/showthread.php?t=224351&highlight=grub+live+cd")

---

### Post by vto80 on 2007-02-11
YES!
It's alive once again!

Thank you all for helping me with this partitioning mess :) 

The answer was to boot from the live cd, chroot, and setup grub. I already edited fstab and menu.lst, it just wasn't searching for menu.lst on the right partition.

vto.

---

