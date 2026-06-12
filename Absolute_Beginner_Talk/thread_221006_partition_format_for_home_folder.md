---
title: "partition format for /home folder?"
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by secallen on 2006-07-22
Hi,

Is it OK to locate the /home folder on a FAT32 partition or does it have to be some other type?

Thank you

---

### Post by lamego on 2006-07-22
Please have in mind that FAT32 can't handle the linux permissions/ownerhsip, meaning if you have several users they will be able to access each others home dir.
Also you may get into some other permissions related problems...

---

### Post by taurus on 2006-07-22
It's not a real good idea to have your /home as FAT32!!!  If you plan to share files between Ubuntu and XP, create a seperate partition and make it as FAT32.  That is the best solution...  ;)

---

### Post by secallen on 2006-07-22
OK, so there's more to /home than just a basic "My DOcuments"? (I really just want my office and image files available to both OSs)

---

### Post by taurus on 2006-07-22
Then create a separate partition and format it as FAT32 (vfat) so you can share it between Ubuntu and XP.  Meanwhile format your /home as ext3 then...

---

