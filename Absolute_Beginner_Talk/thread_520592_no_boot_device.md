---
title: "no boot device"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by pardesi on 2007-08-08
my friend installed fiesty in his computer which previously had XP.he has 512 mb of RAM and 80 GB memory.
it was a perfect installation but now when he reboots his computer the computer asks to insert boot disk and tells that no boot device was detected.he can't even acess his XP.
it's really urgent

---

### Post by overdrank on 2007-08-08
> **pardesi said:**
> my friend installed fiesty in his computer which previously had XP.he has 512 mb of RAM and 80 GB memory.
it was a perfect installation but now when he reboots his computer the computer asks to insert boot disk and tells that no boot device was detected.he can't even acess his XP.
it's really urgent

HI and just a thought, It seems that something might be wrong in the bios. Did your friend have to change the boot order to install?

---

### Post by pardesi on 2007-08-08
no i don't thinki so it was just a normal install from the live CD

---

### Post by Cypher on 2007-08-08
How did he install Ubuntu, using all of the 80 GIG's or making some space for Ubuntu while leaving XP intact? Did he install GRUB and during the installation did he see both Ubuntu and XP listed as boot options?

Pop the Live CD back in and boot back into Ubuntu, open a terminal and type
```

fdisk -l

```
This will list the current partition structure, for anything listed as Linux/EXT3, you can mount it and see what's there..

---

### Post by pardesi on 2007-08-08
actually he lives at a place which is considerably far from where i live and now here it is about to be midnight.
also he can see his XP files in his live cd.
so can u give the probable problems and any codes which i should tell him to check so that tommorow(today) i can tell him to do so ......

---

### Post by overdrank on 2007-08-09
> **pardesi said:**
> actually he lives at a place which is considerably far from where i live and now here it is about to be midnight.
also he can see his XP files in his live cd.
so can u give the probable problems and any codes which i should tell him to check so that tommorow(today) i can tell him to do so ......

HI well if he can see his windows partition and ubuntu partitions fromthe live cd than maybe the grub installation failed. He might reinstall grub by using this thread 
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

