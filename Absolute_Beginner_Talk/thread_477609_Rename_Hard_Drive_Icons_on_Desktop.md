---
title: "Rename Hard Drive Icons on Desktop"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by e30ernest on 2007-06-18
Hi!  How could I rename just the icons of the mounted drives on my desktop?  I'd like to rename "New Volume" to "Media" and "New Volume (2)" to "Backup".  Thanks!

---

### Post by bsharp on 2007-06-18
I'm no expert, but I think the names of the drives are whatever the volume label is.  There is probably a much easier way of doing this, but you *could* reformat them and make the volume labels the names that you want during the format.

---

### Post by coffeecat on 2007-06-18
You don't need to reformat partitions to relabel them, just relabel them. The new partition label will appear under the icon when you next reboot, or if you do:

```
sudo mount -a
```Oh yes. You want to know how to relabel partitions. :lol: Have a look at [this HOWTO]("http://ubuntuforums.org/showthread.php?t=283131"). Scroll down past the fstab bit (it's a long way) until you get to the 'How to Label' bit. There are instructions there for all types of filesystems. And if you want to relabel NTFS or  VFAT/FAT32 partitions from inside Windows (it's actually a bit easier in Windows - sorry about that. :wink: ) have a look at my post in [this thread.]("http://ubuntuforums.org/showthread.php?t=464567") That works equally well for NTFS.

---

### Post by vanadium on 2007-06-18
Also from Places - Computer and the drive properties can you change the "mount points", and the name you give there will be the label of the icon.

---

### Post by bsharp on 2007-06-18
See? there is always an easier way, it is just best to ask here.:D

---

### Post by e30ernest on 2007-06-18
Thanks!  I'll try that how to as soon as I get back from work. :)

---

### Post by philidox on 2008-02-17
Here is a YouTube Video tutorial. Enjoy
[http://www.youtube.com/watch?v=5d0kROklQDY](http://www.youtube.com/watch?v=5d0kROklQDY)

---

### Post by MrKlean on 2008-02-17
or try this !!

I found this while searching...hopefully it will help someone else !! Thanks GIF

To assign a sticky name to a partition I found I could:

1.) On the desktop, open the "Disk-1" (or Disk-2" -- whatever) and verify that it opens the partition that I wanted to name as a Volume permanently.

2.) Back out of it to the desktop.

3.) Right click onthe disk icon.

4.) Select Properties

5.) Select the Volume tab (I didn't select the disk tab -- I wanted volumes -- important since my disk has partitions with a variety of filesystems -- selecting the disk tab and entering filesystem information would have made the system act as if I only had one filesystem)

6.)In the Volumes tab, click on the Settings "twistie" (small triangle) to open settings entry lines.

7.) I entered the mount point as Data-Disk, which was the sticky name I wanted for this partition. I didn't fill in the filesystem type or mount options -- these were shown correctly at the top of the window already.

8.) I rebooted to make the changes happen.

9.) I now had an Icon for "Data-Disk" on my desktop, and it is permanent. I've plugged and unplugged other USB devices, and rebooted to see if I could affect it, but this name is always properly associated with the partition I attached it to.
__________________

---

### Post by philidox on 2008-02-18
> **MrKlean said:**
> or try this !!

I found this while searching...hopefully it will help someone else !! Thanks GIF

To assign a sticky name to a partition I found I could:

1.) On the desktop, open the "Disk-1" (or Disk-2" -- whatever) and verify that it opens the partition that I wanted to name as a Volume permanently.

2.) Back out of it to the desktop.

3.) Right click onthe disk icon.

4.) Select Properties

5.) Select the Volume tab (I didn't select the disk tab -- I wanted volumes -- important since my disk has partitions with a variety of filesystems -- selecting the disk tab and entering filesystem information would have made the system act as if I only had one filesystem)

6.)In the Volumes tab, click on the Settings "twistie" (small triangle) to open settings entry lines.

7.) I entered the mount point as Data-Disk, which was the sticky name I wanted for this partition. I didn't fill in the filesystem type or mount options -- these were shown correctly at the top of the window already.

8.) I rebooted to make the changes happen.

9.) I now had an Icon for "Data-Disk" on my desktop, and it is permanent. I've plugged and unplugged other USB devices, and rebooted to see if I could affect it, but this name is always properly associated with the partition I attached it to.
__________________

I tried it your way and no luck and could you make sure that you went thru all the steps or make a youtube video so the linux community can see exactly what you did.  Thx I like you method alot faster but does not work for me perhaps its something i'm doing wrong?

---

