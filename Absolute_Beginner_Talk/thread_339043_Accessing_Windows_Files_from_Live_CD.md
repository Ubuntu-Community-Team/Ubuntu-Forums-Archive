---
title: "Accessing Windows Files from Live CD"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by brainiac8008 on 2007-01-15
Hi,

I have brought a live cd of Ubuntu 6.06 Dapper Drake to a friend's house. I have started up the disc before Windows and it runs beautifully.  I am wondering though how I can access files on the hard drive.  I know that when you install Ubuntu that it says "hda1" and you can access it, but I just want to look at the files with the live cd.

--Noah

---

### Post by Canis familiaris on 2007-01-15
Open Terminal:
```
sudo nautilus /mnt

```
Create a new folder foldername
Close nautilus
Type exit in terminal.

Then After creating folder in GNOME go to:
System->Administration->Disks
Mount the disk in /mnt/foldername

Then explore in nauilus

:-| You have to repeat these steps ever time, you boot into live-cd

---

