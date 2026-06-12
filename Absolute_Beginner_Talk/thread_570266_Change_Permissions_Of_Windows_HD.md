---
title: "Change Permissions Of Windows HD"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by P3RH4PS on 2007-10-08
I have a dual boot Ubuntu/XP computer each OS has a separate 160GB HD.  Why is it that my Windows drive is read only?  I would like the ability to save my homework and various other files on  that other hard drive and it says I don't have permission to do that.  Is there a way to open it up?  I know it's probably secured so I wont accidentally erase some system files or something, but I'm pretty familiar with the Windows file system.  Any help is much appreciated!

---

### Post by quinnten83 on 2007-10-08
linux by default can not write to NTFS partitions (the partition type that windows uses) that is why you are getting that message.
Install ntfs-3g and you will be able to write to NTFS partitions.

---

### Post by NotoriousMOK on 2007-10-08
Consider creating a FAT32 partition to use for data you intend to share between both OS's.  Windows and Ubuntu can both read/write reliably this way.

---

### Post by P3RH4PS on 2007-10-10
Well, I got the Gnome Partition tool and tried to do that but it wouldn't let me do anything to my Ubuntu drive while it was mounted.  So I got the Gnome Partition LiveCD and tried running that and it just hangs and doesn't fully load...  any suggestions?

Hangs at:

Detecting Adaptec I20 RAID controllers...

---

