---
title: "Cd Drives and 2nd HD not Recognized"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by Warpnow on 2007-04-10
I have 2 cd/DVD drives that were both recognized when I installed Ubuntu and now neither are recognized by the system.

Also, the HD I didn't install ubuntu on...how can I make it work with Ubuntu? Its my bigger drive and I want to know how I can get that space back :D

Thanks for reading the post :D

---

### Post by markusfarkus on 2007-04-10
Check the file fstab in your etc folder. "cd /etc" and open the file "sudo gedit fstab".

You should see those disks listed (ie. hda1 hda3 hdc). 

The cdrom is likely something like this:
/dev/hdc /media/cdrom0 udf, iso9660 user,noauto 0 0

If that is the case it is waiting for a disk to be put in.

You should see any other disks that are listed.  You need to create a mount dir for the disk you wish you mount.

#entry for /dev/hda4
 /dev/hda4    /media/hda4 ext3 default 0 2

That should set up things so that it will automount on a reboot.  To save a reboot do a "sudo mount -a"

Here is a sample fstab file
/dev/hda2  	/  	ext2  	defaults  	1 1
/dev/hdb1 	/home 	ext2 	defaults 	1 2
/dev/cdrom 	/media/cdrom 	auto 	ro,noauto,user,exec 	0 0
/dev/fd0 	/media/floppy 	auto 	rw,noauto,user,sync 	0 0
proc 	/proc 	proc 	defaults 	0 0
/dev/hda1 	swap 	swap 	pri=42 	0 0

---

