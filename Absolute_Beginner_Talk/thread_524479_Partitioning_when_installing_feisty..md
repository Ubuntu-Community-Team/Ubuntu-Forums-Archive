---
title: "Partitioning when installing feisty."
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by Rickraglan on 2007-08-13
The HDD that I want to install Feisty 64bit onto is already patitioned :- C: 49GB, D: 92GB, and Free space 92GB.  C: drive has XP on it. D:drive I use for storage. I would like use 46GB of the free space  for Feisty and allocate the remainder to D; drive. Is this possible ?  If it is can anyone help me.

---

### Post by teeceegee on 2007-08-13
If the freespace is contiguous with the D: drive you should be able to resize this partition to take up some of the freespace. 

Boot the Live CD and use the gparted utility to resize the partition that the D: drive is on (you can run it by opeining a terminal window and typing 'gparted'. Make sure the drive you want to resize is not mounted by Ubuntu. If it is it will probably show up on the desktop as a drive icon and you can right click on it and select unmount.

You may also want to kill the gnome-volume-manager daemon which tried to mount a drive I was resizing the other day before the resize operation was complete causing an error message (but no actual damage). 

Once the resize has completed you can then click on the install and at the appropriate point instruct the installer to use the available freespace on the disk.

tcg

---

### Post by jw5801 on 2007-08-13
Alternatively use the GParted LiveCD to edit your partitions. Create a 46GB ext3 partition for Ubuntu, then boot up the Ubuntu LiveCD and install to that partition. The GParted LiveCD can be found [here](http://gparted.sourceforge.net/livecd.php) and is a much newer version than that found on the Ubuntu CD, plus you won't have any of the issues of gnome-volume-manager trying to mount drives while you're editing them (which can be very annoying).

---

### Post by Rickraglan on 2007-08-13
Hello jw5801, thank you for replying. I used your link and subscribed to SourceForge. Is GParted Live CD a file that can be downloaded onto a CD. I found a lot of info about it, but was unable to download it.

---

### Post by Arisna on 2007-08-13
The GParted Live CD is distributed as an ISO file that you burn as an image to a CD.  You should be able to download the ISO through this page:

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

---

### Post by jw5801 on 2007-08-14
[http://sourceforge.net/project/downloading.php?group_id=115843&use_mirror=optusnet&filename=gparted-livecd-0.3.4-8.iso&49158885](http://sourceforge.net/project/downloading.php?group_id=115843&use_mirror=optusnet&filename=gparted-livecd-0.3.4-8.iso&49158885)
That link will take you straight to the download page (although you might want to select a closer mirror if you're not in Australia), and you'll then need to use a disc burning application to burn the image to CD.

---

### Post by Rickraglan on 2007-09-17
I was trying to install fiesty onto a hard drive that already had 3 partitions on it. I selected  to install onto C: drive 10GB.Instead a 4th partition was created on the freespace. I would like to restore the HDD back to the 3 original partitions. Is this possible. If so can anyone please advise how to achieve this.

---

### Post by jw5801 on 2007-09-18
Delete the partition and expand the old back to where they were...

---

