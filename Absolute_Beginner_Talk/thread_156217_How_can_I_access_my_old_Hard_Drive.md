---
title: "How can I access my old Hard Drive"
date: 2006-04-06
forum: Absolute Beginner Talk
---

### Post by ShadeOfGreen on 2006-04-06
The one with windows on it?  Its on a slave and I can find it I just can't access it.

---

### Post by Old Jimma on 2006-04-06
[QUOTE=ShadeOfGreen]The one with windows on it?  Its on a slave and I can find it I just can't access it.[/QUOTE]

Hi Shade:

I have the same problem, but found some help: read the wiki

[https://wiki.ubuntu.com/InstallingANewHardDrive](https://wiki.ubuntu.com/InstallingANewHardDrive)

My concern (and perhaps yours, also) is that I don't know with certainty that ubunto can't see that drive, or whether I just can't figure out how to see it.

When I do a sudo lshw -C disk, as suggested in the wiki, I can see the drive that I want to access. What I don't know is whether I have access to it without any further intervention as described in the wiki.

All the best,
Phil Smith
Duluth, GA

---

### Post by iluminate on 2006-04-06
[QUOTE=ShadeOfGreen]The one with windows on it?  Its on a slave and I can find it I just can't access it.[/QUOTE]

Hi, 
Donno if you want to it to be mounted all the time. But what I did was to edit the etc/fstab and added the dev name of the disk.
Go to System>>Administraion>>Disks and you will find the name of the disk.

Here is my fstab...

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd1	/home/myhome/xp ntfs ro,user,nls=cp949,utf8,umask=0222,dmask=0000 0 0
/dev/hdd5	/home/myhome/xp1 ntfs ro,user,nls=cp949,utf8,umask=0222,dmask=0000 0 0

Hope it helped.

---

### Post by Old Jimma on 2006-04-06
[QUOTE=ShadeOfGreen]The one with windows on it?  Its on a slave and I can find it I just can't access it.[/QUOTE]


Shade:

The Wiki I cited before works perfectly. Be careful and it will work.

[https://wiki.ubuntu.com/InstallingANewHardDrive](https://wiki.ubuntu.com/InstallingANewHardDrive)

Best regards,
Phil Smith
Duluth, GA

:)

---

