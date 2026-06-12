---
title: "keep disk name from changing - solution ; )"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by MrKlean on 2008-02-03
I found this while searching...hopefully it will help someone else !!  Thanks GIF

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

---

### Post by LowSky on 2008-02-04
Nice write up 

FYI: you can also label partitions with Gparted, and MS window's disk manager. 

Figure I would put that out there

---

### Post by jmap82 on 2008-03-02
> **LowSky said:**
> 
FYI: you can also label partitions with Gparted, and MS window's disk manager. 
You mention that you can label partitions in Gparted, but I don't see where.  Not that it is urgent, but can you point me the right direction?  Thanks.

---

