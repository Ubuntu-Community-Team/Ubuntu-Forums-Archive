---
title: "Is it possible to read Windows files in Linux?"
date: 2005-12-15
forum: Absolute Beginner Talk
---

### Post by Dr. E on 2005-12-15
When my new hard disk arrives I will install Ubuntu on it and leave Windows on the other drive.  Since Open Office is supposed to be able to read the corresponding MS Office files, is there some way to access those files from the hard disk containing Windows or will the two drives speak completely different languages.

---

### Post by Ultimo Aliento on 2005-12-15
You can see and use any file in the windows partiton, as long as you have a linux program that works with that files extensi&#243;n.

If your partition is fat32 format, you could even write files in the windows partition, if the partition is NTFS, the only problem is that you can only read.

The disk manager would automatic mount the partition, thats one of the great new things of breezy :D

---

### Post by monchichi on 2005-12-15
You can mount the Windows drive in Ubuntu, no problemo.

If it is a FAT32 filesystem, you can read and write to the drive.
If it is an NTFS filesystem, you can only read from it.

---

### Post by Dr. E on 2005-12-15
What is the quickest way to see if I have FAT32 or the other kind of files on my Windows hard drive?

---

### Post by heimo on 2005-12-15
Windows and Linux use different filesystems. Usual filesystems for Windows are fat32 and ntfs. Default file system for Ubuntu is ext3 (others include ext2, reiserfs, xfs, jfs). Fortunately Linux understands fat32 very well and is also able to read (but not safe to write) ntfs partitions.

This allows you to set up "shared" disk partition to use from both Windows and Ubuntu, or to use your fat32 Windows partition directly from Ubuntu.

One way to achieve this could be to partition the new disk manually (partitioning disk is part of Ubuntu install process) and make one of the partitions fat32 and use mount point /windows (for example). I believe Windows XP is able to find this new partition automatically, if it's not you can use disk management utility to assign drive letter for this partition. On Ubuntu you will be able to make "shortcut" called link to your desktop (if it doesn't appear automatically) or use the /windows directory directly (some file permissions may need to be changed, we'll be here to help you).

Hopefully this cleared the question. :)

---

### Post by Ultimo Aliento on 2005-12-15
you are in windows or in linux ? ... in windows i think you need to left click on the partition ,  there should be the format... look for any FAT32 or NTFS mention.

---

### Post by heimo on 2005-12-15
[quote=Dr. E]What is the quickest way to see if I have FAT32 or the other kind of files on my Windows hard drive?[/quote] 
Find Disk Management and check the file system name on the partition. For example: right click on My Computer, choose "manage" and click on Storage->Disk Management.

EDIT: See the advice above - that's quicker / easier.

---

### Post by Dr. E on 2005-12-15
[QUOTE=Ultimo Aliento]you are in windows or in linux ? ... in windows i think you need to left click on the partition ,  there should be the format... look for any FAT32 or NTFS mention.[/QUOTE]


Thanks I found it!

---

