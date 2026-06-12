---
title: "cant mount windows during installation"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by mills on 2007-12-11
i think i really messed things up

when trying to install a second harddrive i i was having difficulties trying to figure it out
so i thought i would just reinstall ubuntu and it would mount everything for me like it usually does, but only this time it didnt

during install when it was setting up the partitions it failed to mount the second harddrive so after a while i gave up and unplugged with the intention of backing up all my stuff then doing a fresh install of everything but now i get error 15 from grub 

i have some really important files on my windows partition and iam hoping you guys can help 

what should i do?

just in case i included screenshots partition table and the error
and any help is appreciated

---

### Post by mills on 2007-12-11
maybe this screenshot will help

---

### Post by lswest on 2007-12-11
you need to force mount the drive, and hope to god it doesn't corrupt anything (it shouldn't, but there's always a first time:P) 
first off make a mount point
```
 sudo mkdir /media/disk
```
then run
```
 sudo mount -t ntfs-3g /dev/sda1 /media/disk -o force
```
that should mount the drive on the mountpoint, so that you can access it and back up the stuff you need to.

---

