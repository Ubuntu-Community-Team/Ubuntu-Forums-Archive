---
title: "access Windows while hibernating"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by fallout07 on 2008-01-24
hi there
i have a toshiba laptop with windows xp and ubuntu 7.10. when i still had ubuntu feisty fawn it was possible for me to access windows while hibernating. after upgrading to ubuntu gutsy i can no longer do that. every time i try to mount the c drive it promts me to shut down windows first. is there any way to go around this apart from going back to feisty?
thanks a lot:)

---

### Post by SeanTater on 2008-01-24
I'm not using gutsy (sorry), but if it's giving you a dialog box, you can most likely bypass it in the console.

Something like ```
sudo mount -t vfat /dev/hda /media/hda 
```
vfat could also be ntfs, and hda could be all kinds of things. (like hdb, sda, sdb) 


But I'd give a guess that if windows is hibernating, it's not a good idea to mess with it's files while it's doing it. Be careful.

---

