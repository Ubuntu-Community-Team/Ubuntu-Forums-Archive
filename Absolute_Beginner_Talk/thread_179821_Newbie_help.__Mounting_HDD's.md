---
title: "Newbie help.  Mounting HDD's"
date: 2006-05-20
forum: Absolute Beginner Talk
---

### Post by Kron on 2006-05-20
Well I finally decided to try something Linux flavoured, but I have run into a problem or two.

In summary my problem is this.... I can’t mount the second hard drive; can anyone point me in the right direction? Please.

I completely killed my two HDDs with Darik's Boot and Nuke ("DBAN") before trying to install Kubutnu.  The installation seems to go without any problems, asking me which HDD to install upon, so it could obviously see them both.

I found the HD with the fstab -l command, having seen a post (for another user/problem) that recommended trying cfdisk, to which it responded "FATAL ERROR: Cannot open disk drive" press any key to quit.   I tried another command only to get the response dev/hdb doesn't contain a valid partition table.

Any advise before I quit and go back to Bill Gates and microtheif?  I had three objectives when I started out.
1. Find out more about this Linux stuff :)
2. Use the Linux box as storage device.
3. Work if and how Linux can talk to windows XP across a network.

Obviously all three are interwoven, but if I can work out how to mount the second HDD, then my project is dead in the water.

Many many thanks for any advise, even if it’s to go back to MS.
Cheers
K

---

### Post by catlett on 2006-05-20
[http://www.ubuntuforums.org/showthread.php?t=174562](http://www.ubuntuforums.org/showthread.php?t=174562) That thread should have all your answers. Pay attention to all the posts by Aysiu.

---

### Post by Harleen on 2006-05-20
I don't think this thread will help Kron. As I understand, his 2nd hard drive does not contain a file system or even a valid partition table, so it cannot be mounted.

To use that hard disk, you have to create a partition first. You already found out about cfdisk, but failed with that. You could also do that graphically with qtparted (or gparted, which I haven't tried out yet). Create a partition on the empty disc and format it with ext3 or reiserFS. Afterwards you can follow the hints in the mentioned threads.

---

### Post by catlett on 2006-05-20
Didn't read carefully enough. Did you format and mount the other drive during install? The installer can format and mount any partition, not just the one for installation. You could boot to the installer disk. Choose the second drive during partitioning. When the option dialogue comes up choose to format. It will ask what filesystem. Choose ext3. It will ask a mount point. Choose to manually enter. Enter /media/2nddrive. Keep the mount options at default. Scroll down to done partitioning.
When you get back to the partition table all your Ubuntu partitions will be there as well. Keep them as they are. When you hit on them choose the option "do not format, keep existing data". Then hit on "finish partitionig write changes to disk". It will format the other drive but not your ubuntu. If the install goes to a next stage hit "back" and keep hitting back until you get to the main menu. Scroll down and choose abort installation.

The other option. If you have Ubuntu up and running is gparted. It is a partitioning tool. If it isn't installed you can install gparted with the command ```
sudo apt-get install gparted
``` The interface is pretty easy to understand. You will have a graph-like view of your hard drives. You may have to hit on a drop down box to see the second hard drive. It will be labeled /dev/hdb. Click on the drive and right click for options. Choose to use the entire drive for the partition and format to ext3.
Try the gparted way first. It is easier. If gparted doesn't show up in the menu you can launch the application through the terminal with ```
gksudo gparted
```  The install way is sure to see the disk if gparted doesn't. Once the drive is formatted it can be mounted with Aysiu's instructions.

---

### Post by Kron on 2006-06-07
Catlett

Wanted to say thank you, I tried the gparted route and it seems to have done the trick, not sure if it is mounted yet, but it has been seen and formatted and partitioned, will give Aysiu's instructions a go shortly.

Many thanks for your time and effort.

Kieron

---

