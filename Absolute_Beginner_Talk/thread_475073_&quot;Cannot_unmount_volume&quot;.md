---
title: "&quot;Cannot unmount volume&quot;"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by GiantsFanatic on 2007-06-15
Hi,
I'm very new to Ubuntu and Linux, and I recently decided to install Ubuntu (7.04). Everything is fine, except on the desktop it shows the first partition on my hard drive (sda1, my NTFS formatted, Windows XP partition). I don't want it mounted, and when I right click, unmount, I get, "Cannot unmount the volume," and the details say, "unmount: /media/sda1 mount disagrees with the fstab."

Anyone know how to fix this, and also make it so it doesn't mount automatically on startup?
Help is very much appreciated.
Thanks

---

### Post by Rocket2DMn on 2007-06-15
You can try
```
sudo umount /path/to/partition/mount/point
```

for the source of the problem, two commands for you:
```
fdisk -l
```
This displays the available partitions, mounted or not
then:
```
sudo gedit /etc/fstab
```
This shows you the fstab file it is mentioning, and allows you to edit it.
The source and mount point should match.
You can "comment out" the entry for the Windows partition by placing a "#" at the beginning of the line, this should prevent it from mounting automatically at startup.

---

### Post by GiantsFanatic on 2007-06-15
Alright,
So, I'm able to manually unmount it, but I'm not able to prevent it from mounting at startup. When I head to /etc/fstab, there is already a "#" in front of the line, so I'm kinda confused...
:?

---

### Post by Rocket2DMn on 2007-06-15
Hrmm, your question is very interesting since most of us actually WANT the drive to mount on startup.  Commenting out the correct line should do the trick, but perhaps you need to change some of your ntfs-3g settings.
See if you can find any useful settings by running "ntfs-config".  Being at work, I'm not in front of my Ubuntu laptop to run you through details, but you sound like you know enough to have a look.

If anybody else has input, please give! *BUMP*

---

### Post by zzztownsend on 2007-06-15
Sorry this isn't very helpful but I have the same problem

Mount options under properties on the desktop seem to bear no relation to the relevant entries in fstab

Anyone have any thoughts on what is causing ubuntu to automount even when fstab specifies not to do this?? Not unique to NTFS/FAT/EXT3 file system types


Cheers
Matt

---

### Post by Rocket2DMn on 2007-06-15
This currently running thread talks about having unwanted mount points on the desktop: 
[http://ubuntuforums.org/showthread.php?t=475113](http://ubuntuforums.org/showthread.php?t=475113)
Following these directions should hide the link on the desktop, but it would leave the drive mounted at its respective mount point (which shouldn't be a problem)

---

### Post by zzztownsend on 2007-06-18
thanks for the tip Rocket2dmn

I am now educating myself on what else I can do with gconf-editor


expect a posting later today from me along the lines of 'please help I have tinkered with gconf-editor and broken something important' !!!!

Matt

---

### Post by vanadium on 2007-06-18
You bette rpost your /etc/fstab over here. If it isn there, it won't be mounted, and I think you are not correctly reading your /etc/fstab

* To make sure the partition is not mounted, comment its line in /etc/fstab (for real, this time, i.e., the line beginning with the UUID.

* To have the drive mounted, but not display as an icon: mount the drive on another place, typically /mnt. For this, you change the mount point in /etc/fstab AND create the corresponding appropriate empty directory under /mnt

---

