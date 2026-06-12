---
title: "Help my xp is gone!"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by limelightos on 2007-03-23
i wiped the linux partitions from my 30gb drive while windows was in hibernation and when i boot grub it says ERROR 22 all my files are on windows help me please

---

### Post by floke on 2007-03-23
Fire up a LiveCD and use it to mount your XP partition to see if there's still data on it.
It might be that something has happened to grub, or that grub can;t get to the hibernating XP - you can edit grub from the LiveCD, so once you work out what to do you can resolve it from there.

Good luck

---

### Post by M$LOL on 2007-03-23
You need to fix the MBR of the drive. Pop in the XP cd, boot up into Recovery Console and type fixmbr

---

### Post by deanlinkous on 2007-03-23
boot from a win98 floppy disk or similar and use the command
**fdisk /mbr**
grub will magically disappear and windows should magically act like you never touched linux ;)

---

### Post by limelightos on 2007-03-23
i have knoppix (ughh) running on it i can see all the files on my xp partition

would a windows 95 cd work? i dont have my xp cd as my laptop is 2nd hand

EDIT: lost my '95 cd too...

---

### Post by deanlinkous on 2007-03-23
[http://www.bootdisk.com/](http://www.bootdisk.com/)

---

