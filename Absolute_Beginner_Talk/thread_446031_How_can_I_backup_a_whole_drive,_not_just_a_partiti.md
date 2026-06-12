---
title: "How can I backup a whole drive, not just a partition?"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by gohanssjn on 2007-05-16
I have a drive with Vista and Ubuntu on it and it's perfect at the moment.  Ghost can't do ext3 (not the version I have at least), and partimage seems to only do individual partions.

I don't want to do the partitions individually because I like how they are done now and I don't want to mess with the MBR, which a drive image would restore on failure.

The partitions are NTFS, FAT32, Logical Swap and Logical ext3.

Thanks for any ideas!

---

### Post by starcraft.man on 2007-05-16
Hmmm, I haven't actually tried this program (I use acronis true image, works every time) but I think this program might be what your looking for, its called [AIR]("http://linuxappfinder.com/package/air"). It looks interesting with a nice gui frontend. Give it a shot :)

I will have to look into the backup options some more for other people who ask. Hope that helps. And keep linux app finder bookmarked, its useful :D

---

### Post by irish_flu on 2007-05-16
The only way I can think of to back up multiple partitions "in state", so to speak, would be to mirror the physical drive to another drive (called a RAID 1 setup).

I'm not exactly sure what that does with the MBR, but I know of no other way to back up partition information.

---

### Post by gohanssjn on 2007-05-16
Ok, thanks you two :)

It's just a shame whatever I backup with Ghost 2003 that's in ext3 never works after a restore.

EDIT:  Ok, I feel stupid.  Apparently Ghost 2003 CAN do a disk with ext3.  I must have done something wrong >.>

---

### Post by starcraft.man on 2007-05-16
> **gohanssjn said:**
> Ok, thanks you two :)

It's just a shame whatever I backup with Ghost 2003 that's in ext3 never works after a restore.

Ya I've used ghost before, I didn't like it. It just wasn't a very good program... If you really just need a good program that works simple with a good gui and the above solutions don't help, you may want to get acronis true image, it supports I think every format in existance (reiser ext and the other non windows systems). I put the disclaimer that it is paid, and you would need a windows install to make rescue disk that runs live from boot.

Anyway, best of luck, hope ya get it all worked out. :)

Edit: lol, well whatever works for ya :p

---

### Post by echo $USER on 2007-05-16
You can use rsync, but you need a seperate drive formated w/ ext3.

its as simple as "sudo rsync -a -r / /path/to/external"

At home I have two PCs, I mount a remote partition with NFS, and added rsync to my crontab so every night at 7 it updates the image to the remote partition.

But that doesnt help you since you have NTFS, sorry I brought it up.

---

