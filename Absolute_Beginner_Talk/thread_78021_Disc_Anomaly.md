---
title: "Disc Anomaly?"
date: 2005-10-17
forum: Absolute Beginner Talk
---

### Post by Griff on 2005-10-17
So i have a 20GB partition (hda1) that is currently a fat32 filesystem.  I wanting to install XP here so i need to change it to a ntfs.  Problem is gparted won't allow me.  I keeping getting a generic error message.  Next i tried using the install disc partitioner.  When i try to change the filesystem type, ntfs is not an option.  However, there are 2 places that say fat32.  Should one of these read ntfs?  Why would 2 be listed as fat32?  Sort of stumped here.  Think my comp is trying to tell me something...:rolleyes:

---

### Post by LHZ on 2005-10-18
Linux doesn't really support NTFS. It can read it, but not write to it. An unfortunate corollary of this is is that it's impossible to make a Linux tool that can format a drive to NTFS.

Do you have a windows tool for partitioning? There might be one on the WinXP cd.

---

### Post by blueoyster on 2005-10-18
I know for sure that on the Windows xp cd  allows you to format a partition to NTFS if needed.

---

### Post by Griff on 2005-10-18
Excellent, i should be good now.  Thanks for the quick replies, guys. ;)  Seems like a great community here.

---

