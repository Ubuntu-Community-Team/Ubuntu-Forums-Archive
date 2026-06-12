---
title: "FAT32 Error"
date: 2005-11-28
forum: Absolute Beginner Talk
---

### Post by dpack on 2005-11-28
I have an external USB 2.0 hard drive. I freshly formatted it to FAT32 not 2 weeks ago from Windows. In Ubuntu, I can read and copy from the drive just fine. My problem is I can't write to it. I can create a folder and it will take but copying/moving a file to it won't go. When trying to write a file to it I get the following error: **Error "I/O Error" while copying *filename***. Under the Sys Log it is logging the following: **FAT: Corrupted Directory**. I checked the permissions and I do have Write privileges. I got to have this drive in FAT32 so I can continue to use it in Windows. Anybody seen this issue before or know what I can do about this? Is my only fix for this to re-format the drive to ext3 and give up using my drive with Windows?

---

### Post by ecobuntu on 2005-11-28
what's /etc/fstab say?  can you call it VFAT there?

---

### Post by dpack on 2005-11-28
That file only lists my internal hard drives and my optical drives. My external USB drive is not listed at all.

---

### Post by dpack on 2005-11-28
Also, I pulled up Disks Manager and it lists my USB drive there. It says that the Filesystem is Windows Virtual Fat (vfat).

---

### Post by dpack on 2005-11-29
It seems I'm just screwed if I continue using this drive in FAT32 with Ubuntu. So, I have been looking but can't find a way to reformat this USB drive. When I pull up Disks Manager the Create and Delete buttons on the Partitions tab are grayed out. When I look at the permissions on the drive it says **File Owner: my account** (not root), but at the bottom of the screen it says I'm not the owner and can't change the permissions. How can I be the owner and not the owner at the same time? Okay, whatever you say Ubuntu. How can I reformat this drive to ext3? I don't care if I have to do it through terminal, someone will just need to tell me the code of what to type.

Info you'll probably need to help with the command code:
The drive is currently partitioned into 2 drives.
Device: /dev/sdc
Partition 1: /dev/sdc1  and if you need it, Access Path: /media/MAXTOR_1
Partition 2: /dev/sdc2  and if you need it, Access Path: /media/MAXTOR_2

I want to wipe out the partitions and make one big ext3 drive.

---

