---
title: "folder location - Ubuntu Tweak"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by kneewax on 2008-04-01
In Ubuntu Tweak there is a setting that allows you to change the default location for the folders that usually appear in the 'Places' menu item.  I'd like to make the default locations of these folders /media/sda2 as this is my data partition and I'd rather not have my data on the same partition as the OS.

I have two questions, 

firstly is this an advisable thing to do?  I can't see a problem with it, but would like to get others' more experienced  opinions before doing this.

secondly, the partition I'd like to redirect these folders to is for historical reasons formatted to ntfs - would this be a problem.  Ubuntu reads and writes to the partition without any problem usually.

cheers Kneewax

---

### Post by Oldsoldier2003 on 2008-04-01
> **kneewax said:**
> In Ubuntu Tweak there is a setting that allows you to change the default location for the folders that usually appear in the 'Places' menu item.  I'd like to make the default locations of these folders /media/sda2 as this is my data partition and I'd rather not have my data on the same partition as the OS.

I have two questions, 

firstly is this an advisable thing to do?  I can't see a problem with it, but would like to get others' more experienced  opinions before doing this.

secondly, for historical reasons the partition I'd like to redirect these folders to is for historical reasons formatted to ntfs - would this be a problem.  Ubuntu reads and writes to the partition without any problem usually.

cheers Kneewax

there shouldnt be any problems as long as you don't move /home itself to a NTFS partition. Putting /home on NTFS will cause login problems

---

### Post by kneewax on 2008-04-04
Thanks for this, its very helpful.  I now have a new issue.  I have tried to use Ubuntu Tweak to redirect the 'Places Menu' folders to folders of the same name on my ntfs data partition.  UT won't however select folders on that drive.  It wil let me go through the process of selecting them but won't actually make any changes.  I seem to be able to select folders on the primary partiton OK.  (no help to me though!)

Does anyone know if there is a solution to this.  Is it because the data partition is ntfs or is it because UT won't cross partitions?  

Thanks in advance
Kneewax

---

