---
title: "I've shrunk the XP a bit too much"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by birdseye on 2007-01-13
Whilst installing Ubuntu I shrank the NTFS partition on the disk a bit more than I should. Is there any way of taking a bit of the spare Linux partition and handing it back without having to format complete partitions ? The partition manager that ships with Ubuntu will shrink the NTFS but will not grow it again.

---

### Post by Sef on 2007-01-13
Check out [GParted]("http://gparted.sourceforge.net").  It will shrink and increase NTFS partitions

---

### Post by birdseye on 2007-01-13
Thanks but that l;ooks to be the same tool that ships with ubuntu, and whilst it would both shrink and increase the ntfs partition before I had it format the linux bit, it will now only shrink the ntfs one. Its as if it is a tool for taking ntfs and converting to linux but not for taking linux and formatting it ntfs.

---

### Post by Sef on 2007-01-13
The one that ships with Ubuntu is a stripped down version of Gparted.  Also Gparted on the site is more up to date than the Ubuntu version.

---

### Post by birdseye on 2007-01-13
had another go with gparted - the resize option on the menu is greyed out with all partitions.

---

### Post by birdseye on 2007-01-13
Have donloaded gparted and installed it. Still the same greyed out problem. Bit puzzled:-k

---

### Post by Enverex on 2007-01-13
You need to install 'ntfsprogs'.

---

### Post by hoagie on 2007-01-13
> **birdseye said:**
> Have donloaded gparted and installed it. Still the same greyed out problem. Bit puzzled:-k

You have to unmount the partitions before you edit them. Right-click on them and select unmount then you can resize.:)

---

### Post by bigken on 2007-01-13
just use the gparted liveCD like sef said in the 1st place :rolleyes:

---

### Post by Enverex on 2007-01-13
> **hoagie said:**
> You have to unmount the partitions before you edit them. Right-click on them and select unmount then you can resize.:)

Or that :-#

---

### Post by birdseye on 2007-01-13
> **bigken said:**
> just use the gparted liveCD like sef said in the 1st place :rolleyes:

Yes, I think you're right. I can unmount the ntfs partition but cannot increase it until I've reduced one of the linux ones. I cant unmount the linux partition whilst running linux from the hdd - a bit of a puzzle since the linux partition I want to reduce is the home one rather than the one with the system in it.

so presumably I have to run gparted fom disc but does that mean I have to do so with linux also running from disc rather than hdd?

---

### Post by bigken on 2007-01-13
no just boot from the gparted liveCD ;)

---

