---
title: "Formatting NTFS partition to ext3 after installing ntfs-3g"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by psynyd on 2007-03-14
I want to reformat one of my NTFS partitions to ext3 but gparted won't let me. It cannot find the mount point. I am guessing this has to do with the fact that I am using ntfs-3g. Any solution to the problem without uninstalling ntfs-3g? I want to keep using the other NTFS partitions.

Thanks!

---

### Post by brettg on 2007-03-14
OK, you are a bit confiused it seems. Let me try and help.

gparted doesn't care about mount points, it only deals with devices. What you need to know is the device of the partition in question, ie /dev/hda2

At the console you can do df -h (if it is already mounted as a NTFS partition) to see what device it is on.

In my example the /dev/hda part refers to the physical hard disk and the number 2 refers to the partition number on the disk.

Once you have identified that you can type sudo fdisk /dev/hda (or whatever, note the missing numeral from the end, we are selecting the HDD here) which will open fdisk for editing the HD. You might want to 'sudo unmount /dev/hda2' if it is already mounted.

Then all you need to do is press 'p' to list partitions (confirming you are on the the right HD) and then press 'd' for 'delete' and then the partition number (2 in this example).

Then you can press 'n' for 'new' and follow the prompts, followed by 't' for 'type' and enter 83 for type=linux.

Then you press 'w' (for 'write') to write it all to disk then you are finished partitioning. 

You may or may not need to reboot at this point.

Then do 'sudo mkfs t=ext3 /dev/hda2' and you are done. Then you just need to mount the drive either manually or by entering it in /etc/fstab and doing mount -all

WARNING: If you repartition or reformat the wrong drive or partition you CANNOT GO BACK. 

You could very well bork your system. You have been warned.

---

### Post by psynyd on 2007-03-14
Wow. sonds good! thanks!

I'll try it out over the weekend and let you know. But yeah, gnome partition mamanager does say that it cannot detect the mount points. However since I dont need to know the points, I guess this should work.

THanks again!

---

