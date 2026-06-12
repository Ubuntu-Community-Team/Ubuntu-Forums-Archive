---
title: "problem burning cd or dvd no disc found"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by Ubukanuba on 2007-11-24
I am trying to burn an image .iso to disc and i cant get it to read any of my blank disks.  The others i have to mount manually.  No idea what to do.  It just keeps saying insert blank disc....

---

### Post by Ubukanuba on 2007-11-24
set dma to 1 in terminal but didnt work....anyone know why no blank dvd's or cd's are showing up in the dvdr?

---

### Post by Fixman on 2007-11-24
m...try downloading k3b, maybe that programs makes it work

```
 sudo aptitude install k3b
```

---

### Post by Ubukanuba on 2007-11-24
already installed that, but i just found out that by right clicking on my dvdr drive that the drive properties are all 3 set to read only and it says:

"sorry the permission could not be changed: Sorry, couldn't change the permissions of "CD-RW/DVD±RW Drive".

how do I fix this??

---

### Post by Ubukanuba on 2007-11-24
> **Ubukanuba said:**
> already installed that, but i just found out that by right clicking on my dvdr drive that the drive properties are all 3 set to read only and it says:

"sorry the permission could not be changed: Sorry, couldn't change the permissions of "CD-RW/DVD±RW Drive".

how do I fix this??

Anyone know how to change the permissions?

---

### Post by NightCrawler03X on 2007-12-04
This happened for me too.

Then I remembered that ubuntu automounts cd/dvd.
You need raw access, that is, they can't be mounted.

If, for example, you have a dvd in a dvd-rom drive, and a blank dvd in a dvdrw drive, unmount the two drives:

Go to your terminal
```
umount /dev/scd0
umount /dev/scd1
```
The "/dev/scd0" and "/dev/scd1" might be different for you (that is, you have a different file controlling your drives.

Most, if not all, cd/dvd authoring software on linux requires RAW access the any drive your using, so you *must* unmount the drives you wish to use, first.

Regards

---

