---
title: "DVD drive wont open when eject button is pushed"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by robfindlay on 2008-01-30
I'm running gutsy, and this seems to happen sometimes with or without a disk. 

Is there a command line to FORCE the drive to unmount anything that might be mounted or at least to eject the tray? 


-R

---

### Post by Whiffle on 2008-01-30
eject /dev/whatever/it/s

---

### Post by PmDematagoda on 2008-01-30
You can also use:-
```
eject cdrom*
```
* replaced by the number of the CD-ROM as given by the Linux system.

---

### Post by robfindlay on 2008-01-30
No dice, neither does anything or returns an error message.

---

### Post by robfindlay on 2008-01-30
SPOKE TO SOON!

Some rogue proccess had the drive in use.

---

