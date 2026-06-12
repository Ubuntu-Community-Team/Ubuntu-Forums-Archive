---
title: "Moving from XP Raid5 to Linux Raid5, help!"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by webjames on 2006-11-12
Hi, i would call myself a beginner although have gone through a few Linux installations in the past. this is my current setup:
XP with 5 hdds,
c: drive is a 114gb sata hard drive
x: drive is a xp software raid5 array consisting of 4 250gb disks.

NOTE: i do have an Sil3114 card, however it's a fakeRAID card so i decided to use it as a sata base controller and use software raid.

this xp software raid5 array has lots of data on that i want to keep.

my problem is i am fed up with XP, i use open office anyway and think it's about time for an upgrade. how can i go about moving my xp raid5 set to a Linux software raid set?
is Ubuntu suitable? i have heard of MD is this what i should be using? what should i mount the array as? or should i keep it FAT32 windows?
i ought to add that the raid5 file system is NTFS :(
thanks for all your support,

Regards, James

PS i have attached a screen shot of the disk management screen in XP

---

### Post by JonnyR on 2006-11-20
Hey,

I just went through a similar process to you (I had a 4x 320gb Raid-5 Array in Windows XP).  I'm afraid I don't know of any way that Linux can read NTFS Raid Volumes.

I ended up purchasing a 320gb USB External Hard Disk Drive and dumping as much info onto that as I could (I also used the HDD in my Xbox, Laptop, pretty much any storage I could get my hands on!).  Once everything was "backed up" I formatted the 4x 320gb HDD's and create a new Linux Raid-5 set.

Good luck!

---

### Post by webjames on 2006-11-22
yeah thats pretty much exactly what i did! gotta love the xbox mods! :)

---

