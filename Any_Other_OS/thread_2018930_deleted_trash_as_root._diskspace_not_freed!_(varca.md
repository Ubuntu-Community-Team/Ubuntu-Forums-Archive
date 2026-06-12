---
title: "deleted trash as root. diskspace not freed! (/var/cache/apt/archives)"
date: 2012-07-06
forum: Any Other OS
---

### Post by slixz85 on 2012-07-06
hi. i recently deleted about 1gig of files from /var/cache/apt/archives as root because i tried as normal user and it said permission denied. so immediately after deleting the files i clicked on trash under pcmanfm while still root and it says operation not supported. i am currently using bodhi 1.4 stable so i noticed the 1gb never cleared though from looking at the bottom of pcmanfm status bar.

also another small issue when i try to unmount a drive with pcmanfm it says "authentication is required" if i click open folder as root then the partitions don't even show up then to try and unmount that way. i know i can do this by terminal possibly but i like gui best. what i am used too.

thanks to any help/input

this is 10.04lts with e17

---

### Post by oldos2er on 2012-07-07
Moved to Other OS/Distro Talk.

---

### Post by buzzingrobot on 2012-07-08
> **slixz85 said:**
> hi. i recently deleted about 1gig of files from /var/cache/apt/archives as root because i tried as normal user and it said permission denied. so immediately after deleting the files i clicked on trash under pcmanfm while still root and it says operation not supported. i am currently using bodhi 1.4 stable so i noticed the 1gb never cleared though from looking at the bottom of pcmanfm status bar.

also another small issue when i try to unmount a drive with pcmanfm it says "authentication is required" if i click open folder as root then the partitions don't even show up then to try and unmount that way. i know i can do this by terminal possibly but i like gui best. what i am used too.


I don't use Bodhi or pcmanfm, but you, in your guise as the regular user you are logged in as, don't have permission to delete files you don't own.

The files in /var/cache/apt/archives are put their by apt-get when you install packages.  It is, as it says, a cache.  If you want to delete those files, execute "sudo apt-get clean". If you need to reinstall one of those deleted packages, you will need to download it again.

---

