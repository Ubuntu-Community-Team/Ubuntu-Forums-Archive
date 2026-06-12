---
title: "Read only harddisk"
date: 2006-10-08
forum: Absolute Beginner Talk
---

### Post by Mazen on 2006-10-08
i have ubuntu 6.06 with WinXP(dual Boot) and i have an external hard drive, both the external drive and the xp drive are NTFS and i can't write on them from Ubuntu! y is that? they say i need permission....where do i get that permission!??thanks

---

### Post by gn2 on 2006-10-08
Irrespective of permission, Ubuntu will not write to NTFS without assistance of additional (expiremental) software..... Hazardous.

Will read/write to Fat32 though.

---

### Post by Mazen on 2006-10-08
What are those software? and you said Hazardous....so you don't advice them?
and one more thing, what's the MAIN difference between FAT32 and NTFS because if there's not alot of disadvantages to FAT over NTFS i can reformat my external so i can use it as a common read/write drive or something.
Thanks

---

### Post by gn2 on 2006-10-08
Would advise Fat32 for external drive, disadvantages are 4gb file size limit, (DVD ISO's are out) and fragmentation.

---

### Post by Mazen on 2006-10-08
and what aboput those programs? cuz i can't "afford" 4GB files beeing out!

---

### Post by CatKiller on 2006-10-08
There is a driver to give XP ext3 support. I don't know how attractive an option that is to you - you'd have to install it on each Windows machine you want to access that drive.

---

### Post by gn2 on 2006-10-08
You can copy and paste in one direction from either drive. 
It's writing from one to the other that's the snag.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

[http://www.jankratochvil.net/project/captive/](http://www.jankratochvil.net/project/captive/)

---

### Post by TheGrinch on 2006-11-17
Mazen, I had the same problem until I installed Xandros Home Edition-Premium (you can register for a trial version) on another PC & connected the external hard drive. Xandros has the built in ability to write to NTFS partitions. To my surprise when I connected the external hard drive to my Windows XP PC & created a share for it, I could then connect to the share from my Ubuntu PC & write to the hard drive.

---

