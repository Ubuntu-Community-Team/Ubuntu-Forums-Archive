---
title: "Can't see Drive?"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by aheicher on 2007-07-26
Hi All:
I just got a brand new external 80GB hard drive, and I installed Ubuntu on it.  However, I also want to move some of my movies and music to that drive, BUT I want them to still be accessable from the Windows Xp side (to get music into iTunes for my iPod)  When I first got the drive, I partitioned it and formatted it from the Windows side, and then did the same from Ubuntu.  How can I view the files on the drive in My Computer from Windows?  (Dell Dimension 3000, Windows XP, Ubuntu Desktop v7.0.4, Beyond Micro Mobile Disk 80GB External Hard Drive)  
Also with this question-Is there a partition manager I can get to from the Ubuntu side?
Thanks much
Heicher

---

### Post by FleetAdmiral74 on 2007-07-26
You partitioned it twice? Well there is your problem...what did you partition it as? If you used ext3, Windows cannot read that without extra software. If you did NTFS, Ubuntu cannot read that without extra stuff. If you use FAT32, both can Read and Write w/o anything extra.

EDIT: use gParted. You can access if off the Ubuntu live CD, a gParted LiveCD, or when running Ubuntu System-Administration.

---

### Post by Rocket2DMn on 2007-07-26
Only thing with FAT32 is that the file size can't be greater than 4GB, and that can be a problem with files like DVD images or large movie files.
ntfs-3g works well for reading and writing files on an ntfs partition, and the driver from [http://www.fs-driver.org](http://www.fs-driver.org) allows you to read ext2/3 in Windows.

---

### Post by aheicher on 2007-07-26
what is the software-I used ext3
would this work-http://www.diskinternals.com/linux-reader/

---

### Post by Rocket2DMn on 2007-07-26
That program only allows you to read file, you cannot write to the ext3 system. I suggest the driver I linked to above - it will mount an ext3 file system (linux) into Windows as an ext2.  So it's not perfect, but it's as close as you can get.
The alternative is to format the drive with NTFS and use ntfs-3g to read/write from Ubuntu.  FAT32 is also an option if you don't think you will be using really large files (over 4 GB).  This would require no extra software/drivers in either Windows or Ubuntu

---

### Post by aheicher on 2007-07-26
I got it, thank you all!

---

