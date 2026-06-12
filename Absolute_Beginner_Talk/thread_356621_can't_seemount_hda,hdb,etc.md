---
title: "can't see/mount hda,hdb,etc"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by Curious65 on 2007-02-08
when i run the live CD (either version 6.06 or 6.10 of either Ubuntu or Kubuntu) on 5 different computers from a Plll with 356MB RAM to a AMD64 with 1 GB of RAM i don't see the HDDs or CD/DVD drives. and even if i can find them in system:/media/hda1 they won't mount. i get "mount: can't find /dev/hda1 in /etc/fstab or /etc/mtab". and clicking the installer from the desktop produces no result. probably because there's no where to install to. 

if Knoppix is used i see the HDDs. but i really want to install either Ubuntu or Kubuntu.

---

### Post by Curious65 on 2007-02-08
tried the installer feature again a little while ago and this time it saw the HDDs on one of my computers. didn't let it finish since this wasn't the box Ubuntu was going on but i do know that it should work. 

thanks for having this forum. it got me refocused.

---

### Post by dwblas on 2007-02-08
> mount: can't find /dev/hda1 in /etc/fstab or /etc/mtab"You have to provide a mount point since it isn't in /etc/fstab
mount /dev/hda1 /media/hda1 (or whatever).  That is assuming that hda1 is a filesystem that Linux can recognize.

---

