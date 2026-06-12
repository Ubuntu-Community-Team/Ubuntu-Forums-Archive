---
title: "[SOLVED] 32bit to 64bit"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by offroad64 on 2007-10-16
Thanks in advance.
I want to switch from 32bit Fiesty to 64bit Gutsy. I already know that I can't just upgrade. Is it possible to backup all my user data and reintegrate the backup into the fresh 64bit install? So I could pick up sort of were I left off with Fiesty. If so what files and folders do I need to backup?
Any help would be great.
Jeff.

---

### Post by LowSky on 2007-10-16
i would just save you improtant document and other files.

Most of the programs will need to be reinstalled to work correctly with 64bit ubuntu

---

### Post by Kilz on 2007-10-16
> **offroad64 said:**
> Thanks in advance.
I want to switch from 32bit Fiesty to 64bit Gutsy. I already know that I can't just upgrade. Is it possible to backup all my user data and reintegrate the backup into the fresh 64bit install? So I could pick up sort of were I left off with Fiesty. If so what files and folders do I need to backup?
Any help would be great.
Jeff.


If you have a separate home partition you just need to mount it in the new install. Dont delete it. 
If you dont have a separate home partition. You could install Gutsy to a new partition if you have room, then mount the old feisty partition to a folder, then copy the contents of home to home. Unmount the old install, and delete it once you know everything is ok.

---

