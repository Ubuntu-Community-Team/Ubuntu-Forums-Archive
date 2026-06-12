---
title: "Can't resize windows partition with gparted"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by kei-clone on 2008-03-18
I'm running the gparted live cd and attempting to repartition my hard drive like so:
[http://img410.imageshack.us/img410/3016/gpartedoa7.jpg](http://img410.imageshack.us/img410/3016/gpartedoa7.jpg)


when I try to apply this, gparted gives me an error. I have included the details below:
[http://pastebin.ca/948354](http://pastebin.ca/948354)

Can anyone help me with this? Should I defrag and try again?

also the last partition should be a swap partition, forgot to do that heh. will make sure that happens next time.

---

### Post by MidEvilHungarian on 2008-03-18
i hope you not trying to repartition a the drive that the windows system is on.
I did that before and after reboot, windows wouldn't start and i had to reinstall the whole thing. As far as repartition with live CD will never work because the fstab can not be changed on the CD, later you will come across editing the fstab file if you want to write to FAT/NTFS partition. I suggest that you get your hand on a hard drive and install ubuntu on that. Check to see if you can boot windows now.

---

### Post by Hospadar on 2008-03-18
If you are resizing anything but a brand-new windows partition, you should first de-frag it (from windows, several times) and run chkdisk on it.  I think you might even be able to resize the partiton in windows (right click my computer->manage), I'm not sure though, I think I heard somewhere that XP can't do that.

Since it looks like you are partioning the system to prepare it for a new ubuntu installation, you shouldn't have anything to worry about in terms of your fstab (since it doesn't even exist yet)

Besides that, I think your next best option would be (after backing up all your important windows data in case it disappears) to research the command line method to resize your ntfs partition (using the "ntfsresize" tool)  You can run "man ntfsresize" to learn about the command line options, or I'm sure if you google around you can find some more info and maybe some tutorials.  I suggest this because I think it will give you a clearer idea of what is wrong than the output from gparted (if it doesn't just work).

Also, make sure you do any resizing operations after a clean windows shutdown.

If you can get that to work for you, then go ahead and use gparted to make your linux partitons (or just use the partitioner in the installer)

---

### Post by Xarok on 2008-03-18
> **MidEvilHungarian said:**
> i hope you not trying to repartition a the drive that the windows system is on.
I did that before and after reboot, windows wouldn't start and i had to reinstall the whole thing. As far as repartition with live CD will never work because the fstab can not be changed on the CD, later you will come across editing the fstab file if you want to write to FAT/NTFS partition. I suggest that you get your hand on a hard drive and install ubuntu on that. Check to see if you can boot windows now.

There's no way to increase the size of a partition that the Windows system is on?

What I'm trying to do currently is clone my Windows HDD onto a larger HDD and then resize the cloned partition to fill the larger HDD...
I was planning on using Gparted also....
Is this not possible?

---

### Post by Sef on 2008-03-18
> What I'm trying to do currently is clone my Windows HDD onto a larger HDD and then resize the cloned partition to fill the larger HDD...
I was planning on using Gparted also....
Is this not possible?

[GParted-Clonezilla Live CD]("http://gpartedclonz.tuxfamily.org/index.php") can partition and clone hard drives.

---

