---
title: "Format second drive as fat32?"
date: 2005-10-30
forum: Absolute Beginner Talk
---

### Post by Darrin on 2005-10-30
I have a second HD which I use just for file backup (Pictures, documents, etc..)which is in NTFS format and I understand that in order to read and write on that drive from Linux it needs to be in fat32 format.  I dual boot ubuntu/winxp right now and want to be able to add files to that drive regardless of whether or not im in windows or ubuntu. How do I wipe out the whole drive and put it in fat32?

---

### Post by Kapre on 2005-10-30
[QUOTE=Darrin]I have a second HD which I use just for file backup (Pictures, documents, etc..)which is in NTFS format and I understand that in order to read and write on that drive from Linux it needs to be in fat32 format.  I dual boot ubuntu/winxp right now and want to be able to add files to that drive regardless of whether or not im in windows or ubuntu. How do I wipe out the whole drive and put it in fat32?[/QUOTE]

I would suggest re-formatting it. If you can browse thru it from your M$XP, then just format it directly then mount it on your Ubuntu (editing the fstab - using the [guide]("http://www.ubuntuguide.org/#mountunmountfat"). Or if you can browse thru it on your Ubuntu (System---->Administration------>Disks), just format it and setting the system as FAT32.

K

---

