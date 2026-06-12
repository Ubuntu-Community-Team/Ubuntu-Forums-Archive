---
title: "Partition Problem"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by federicotedin on 2007-06-26
I hope this post gets an answer as i relly need it.  I currently have XP in my pc in a 160GB hard disk.  When I try to install Ubuntu with the CD after reboot, the installation thinks the HD is empty.  I need help to create a partition, as i don't know how to do it, when i tried to create a partition with the installation it produced an error, any help?Can i create a partition with a free, non-trial program? If i can, how does it have to be?
Thanks in advance

---

### Post by drowner on 2007-06-26
Are you using the liveCD or the alternate CD?

---

### Post by federicotedin on 2007-06-26
The live CD, downloaded it straight from the official webpage (not the alternate that i know of)

---

### Post by drowner on 2007-06-26
Oh ok, so the liveCD runs?

Open a terminal and type:

sudo fdisk -l

and show us what it says

---

### Post by Maxtorm on 2007-06-26
Another alternative is to download the GParted Live CD ([http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)) and resize your Windows XP partition.  Shrink the XP partition to, for example, half the physical disk size and leave the remainder as unpartitioned space. When you get to the stage in the Ubuntu install where it is asks about disk partitioning, choose to use the largest free contiguous space on the disk.  This should install Ubuntu into the unpartitioned space.   **Normal precautions apply with respect to backing up your XP partition before doing any of this.**

---

### Post by Smandola on 2007-06-26
If you use GParted, there are some instructions you should follow to compress/clean-up your windows partition.    This may be a useful post to read through first... 
[http://ubuntuforums.org/showthread.php?t=224907](http://ubuntuforums.org/showthread.php?t=224907)

Hope this helps.

---

