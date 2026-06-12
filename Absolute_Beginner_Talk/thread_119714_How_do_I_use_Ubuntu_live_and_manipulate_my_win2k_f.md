---
title: "How do I use Ubuntu live and manipulate my win2k files?"
date: 2006-01-20
forum: Absolute Beginner Talk
---

### Post by Tardicus on 2006-01-20
Hey all,

Long story short, my Windows 2000 prof installation died.  Repairing /w emergency repair disks and such diddnt work.  I recently got Ubuntu live to see if I could transfer some files (some photos and essays) from one hard drive to another (call em hard drive 1 and 2 for simplicity) before I reformat drive 1 (with windows 2000...again).  I plan on installing Ubuntu on hard drive 2 after I reinstall windows on drive 1.

How can I use Ubuntu Live to move some of my old files from drive 1 to drive 2 (or can I)?

Can I install ubuntu on hard drive 2 and still access files on both hard drives?  Hard drive 1 and 2 are currently formatted /w NTFS.


Thanks in advance for your help,
-Jason

---

### Post by mcduck on 2006-01-20
you can read and copy files from NTFS, but you can't write to it.

If you want to share a partition bwetween Linux and Windows, FAT is the way to go.

---

### Post by Tardicus on 2006-01-20
[QUOTE=mcduck]you can read and copy files from NTFS, but you can't write to it.

If you want to share a partition bwetween Linux and Windows, FAT is the way to go.[/QUOTE]

How would I go about reading/copying my NTFS files using Ubuntu? :confused:

---

### Post by Herman on 2006-01-20
> I plan on installing Ubuntu on hard drive 2 after I reinstall windows on drive 1. In my opinion, the fastest and easiest way for you would be to go ahead and install Ubuntu Breezy on hard drive 2. It will probably take you around half an hour or forty-five minutes depending on your computer. See my first 'sig link' for details on how to install.
Then when you boot 'Breezy', simply copy the files into 'Breezy' by mounting the partition if it isn't already automatically mounted for you. 
Then re-install your Windows 2000. If you can, install Windows 2000 with a FAT32 filesystem, it's better for dual booting. You will have to re-install GRUB (Ubuntu's bootloader after that, there are several methods for doing that, here's one, [http://www.ubuntuforums.org/showthread.php?t=114332]("http://www.ubuntuforums.org/showthread.php?t=114332"). Then you can just paste your files back into it. Otherwise, if you are forced to make your Windows 2000 on ntfs, you can still transfer your files by CD-ROM or some other way.

If you insist, we can explain how to use the Live CD like you asked , but first you'll need to do as mcduck said and reformat your hard drive 2 as FAT32. It will take a little more effort to explain and to follow, that's all, and there will be no point if you are going to install Ubuntu afterwards anyway.

Edit: Here's a thread that already describes what you originally asked for: (but on FAT32). [http://www.ubuntuforums.org/showthread.php?t=108356&highlight=herman](http://www.ubuntuforums.org/showthread.php?t=108356&highlight=herman)

---

