---
title: "dual boot"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by phanipalagummi on 2008-03-28
I want to dual boot my system(linux,XP),and please tell how to view 
the contents of ubuntu when i be in XP and vice versa.
Please give me the material regarding this

---

### Post by ph1 on 2008-03-28
Well, since Windows uses an NTFS filesystem and Linux uses (by default) and ext2 or ext3 filesystem, Linux can see Windows, but Windows can't see Linux without an application that can read ext2 and ext3 partitions.  So if you're planning on having one large partition for storage and keeping your OS on another smaller one, use Windows for storage.  (Even better would be to have three partitions, one for Windows OS, one for Linux OS, and one "neutral" one for storage, in an NTFS or FAT format, though I'd prefer NTFS.)

To view your Windows partition in Linux, you just go under "Computer," right click on the partition that contains Windows and/or your data, and click "mount disk."  You can automate this using fstab or using a sessions command.

---

### Post by wolfen69 on 2008-03-28
get [http://www.fs-driver.org/](http://www.fs-driver.org/) for xp to see linux partitions.

nothing is needed for ubuntu to see ntfs.

---

### Post by Duck2006 on 2008-03-28
This is on installing.

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

As for reading win drive you will be able after you install ubuntu. As for writing to ntfs drives you need to install ntfs-3g drivers.

---

