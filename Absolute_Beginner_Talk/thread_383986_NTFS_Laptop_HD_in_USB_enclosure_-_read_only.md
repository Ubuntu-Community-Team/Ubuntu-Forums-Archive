---
title: "NTFS Laptop HD in USB enclosure - read only"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by getut on 2007-03-13
Hello...

I have an 80 GB Laptop hard drive that is formatted NTFS installed in an external USB 2.0 enclosure and every time I plug it in it automounts as read only.

I already have another permanent ntfs-3g stuff loaded because I can read AND write to my NTFS partition.

How can I get my USB drive to automount read/write instead of just read only when I plug it in?

---

### Post by euler_fan on 2007-03-13
Is it worth the effort to you to back up the data (I assume you have not completely filled the drive) and reformat it to FAT32? This may seem odd, but I have an external drive that I have no problems with out of the box (its a western digital and I have not reformatted it.)

Otherwise, I am not well enough versed in editing permissions, etc, to assist you with ntfs-3g.

Good luck.

---

### Post by getut on 2007-03-14
That really does seem like moving backwards going to fat32.

If it wasn't for needing to share the drive between a couple Ubuntu machines and a couple XP machines, I'd probably go to EXT3 on it.

Is there no way I can make the automount when the drive is plugged in work in a read/write fashion?

---

### Post by geirha on 2007-03-14
This page: [http://doc.gwos.org/index.php/NTFS-3g](http://doc.gwos.org/index.php/NTFS-3g) has a section about NTFS Removable drives. It tells you to have a look in a file. Does it give any hints on how to change the policy from ro to rw?

(I haven't tried the ntfs-3g packages myself, as I don't use ntfs at all)

---

