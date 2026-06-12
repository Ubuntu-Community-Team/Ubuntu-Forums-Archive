---
title: "Question about formating Xtra drive space properly while dual booting"
date: 2005-11-11
forum: Absolute Beginner Talk
---

### Post by ausm on 2005-11-11
I am currently running WinXP pro and Ubuntu Breezy Badger on 2 seperate hard drives configured in the following manor.

Drive 1: 200 Gig Drive has WinXP on the primary partition which is a 100 gig and it has 100 gig of free space I would like to utilize.

Drive 2: 120 Gig totally devoted to Ubuntu Linux

I want to utilize this drive in both OS'S so what is the proper way to do it?

1)Using Partion Magic in Winblows?

2)Using the Disk administration GUI in Ubuntu and slect the VFAT format?

TIA,

Ausm

---

### Post by Kyral on 2005-11-11
Purdy much, though I heard that the Disk Admin is a little sketchy.

The surefire way to get it working though would be to

```
sudo mkfs.vfat -F 32 /dev/XXXX
```where XXXX is the partition (hda1, hda2, etc)

This puts a FAT32 FS on the partition. Then you have to make a mountpoint.

```
sudo mkdir /media/(pick a name, I suggest shared for this)
```

Then crack open /etc/fstab with

```
sudo gedit /etc/fstab
```

and add this line

```
/dev/XXXX /media/shared vfat defaults,user,rw,auto,umask=1000,gid=000 0 0
```

Then just save it and it SHOULD mount with

```
mount /media/shared
```

---

### Post by ausm on 2005-11-11
Thx Kyral for the help!


Ausm

---

### Post by Kyral on 2005-11-11
Did it work? ;P

(Assuming yes, but never know)

---

### Post by ausm on 2005-11-11
Actually I am at work right now and won't be able to try it until I get home ;)

Ausm

---

