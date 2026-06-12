---
title: "Is that possible to samba hard disks with a CD booted ubuntu?"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by cdrw on 2007-07-25
Greetings.

I have got a machine with two hard disks and all of them are XP NTFS. They are D: drives of my previous systems thus unbootable. Is that possible that I CD boot ubuntu, then samba the two hard disks so that I can user my XP laptop to back things up?

regards,

cdrw

---

### Post by tcpip4lyfe on 2007-07-25
Well Samba is used for networking so the correct question is "can I mount a NTFS drive off the live CD."

You can mount a NTFS drive off the live CD and back it up to another HD or a USB drive as follows:

Boot off the live CD.
Open a terminal.

To find out what /dev your NTFS drive is:

```
sudo fdisk -l
```
Should say NTFS on your drive you want to back up.

Then we need to make a directory to mount the ntfs drive in:

```
sudo mkdir /media/backup
```

Then its time to mount it:

```
sudo mount -t ntfs /dev/hda# /media/backup
```
                                                       
/*\replace # with the numgber of your ntfs drive you found in fdisk -l (ex: /dev/hda1)

Should work.  Then you can just backup your data onto another disk or network server.
 
Make your you unmount the drive before you shut down.  You can just right click on the mounted drive and select unmount.

 
Good luck!

---

### Post by cdrw on 2007-07-29
thanks for the information tcpip4ly4e:popcorn:

---

