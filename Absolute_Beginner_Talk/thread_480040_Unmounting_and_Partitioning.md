---
title: "Unmounting and Partitioning"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by saxuntu on 2007-06-21
You know i'm loving Linux, but this ntfs crap is driving me nuts. My setup is dual boot with two internal hard drives: 1) 80 GB Windows XP (one partition ntfs, the recovery partion fat32), 2) 14 GB Ubuntu. After spending a day trying to access my ntfs partition and finally doing it, somehow,  i now want to resize the ntfs partition so i can have more linux space. 

To those who say "But you now have access to your stuff, y the hassle?" I say i want to write to this space and half the stuff i read says writing to ntfs in linux is a bad idea and the other half says no problem. I figured i'd play it safe. 

Anyway, any help would be appreciated. Thanks.

---

### Post by AriciU on 2007-06-21
I'm writing to NTFS from Linux without any problems so i wouldn't really worry about it.

The simplest way to resize your partition would be to boot windows and use a windows based partition manager to resize... 

You could try to do it from "gparted" in Linux but it would be easier doing it thru windows IMO.

---

### Post by bodhi.zazen on 2007-06-21
> **saxuntu said:**
> You know i'm loving Linux, but this ntfs crap is driving me nuts. My setup is dual boot with two internal hard drives: 1) 80 GB Windows XP (one partition ntfs, the recovery partion fat32), 2) 14 GB Ubuntu. After spending a day trying to access my ntfs partition and finally doing it, somehow,  i now want to resize the ntfs partition so i can have more linux space. 

To those who say "But you now have access to your stuff, y the hassle?" I say i want to write to this space and half the stuff i read says writing to ntfs in linux is a bad idea and the other half says no problem. I figured i'd play it safe. 

Anyway, any help would be appreciated. Thanks.

The drivers to read/write to ntfs are now considered to be reasonably reliable, it depends on your level of paranoia/safety.

To resize your partitions I advise gparted. You need to unmount the partitions before you  resize, so best to use a live CD. Gparted is on the desktop CD.

Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)

---

### Post by saxuntu on 2007-06-21
Never even attempted in Windows. Any ideas on where to find a HOWTO or the like?

thanks for the help.

---

### Post by saxuntu on 2007-06-21
Used LiveCD of Feisty and Gparted, worked like a charm. Thanks.

---

