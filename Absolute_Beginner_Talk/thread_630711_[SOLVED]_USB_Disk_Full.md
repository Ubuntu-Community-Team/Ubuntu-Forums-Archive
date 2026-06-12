---
title: "[SOLVED] USB Disk Full"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by El_Matthews on 2007-12-03
Gents,

I have a USB disk from 75GB and when its mounted in Linux it always says that it is full.

hereby the output of df -h
/dev/sdb5              75G   75G  192K 100% /media/USBDISK

If I check with disk usage analyzer only 65.6 GB is used. 

When I use in Windows I have no problem to see the free space. I also checked if there is no hidden trash files but nothing found. Why is Linux seeing this disk as full? What can I do to solve this without formating my disk again.

Greetings

Matthews

PS: the file system is fat32 if this can help.

---

### Post by philinux on 2007-12-03
My 4 gig pen drive when formatted only has 3.7 gig available this is due to manufactures quoting misleading info and the computer using its proper binary calulator. no big deal.

---

### Post by El_Matthews on 2007-12-04
This is not the problem, it's a disk of 80GB but after format 75GB.

The problem is that linux doesn't see the 10gb free space and windows does.

---

### Post by laidback on 2007-12-04
Check its wastebin. When you delete the files are still there unless you clear them for good. Shift & delete   deletes without putting file into wastebin.

---

### Post by caclratm on 2007-12-04
I had the same problem with a 1gb pendrive, and I had to format. Of course, backing up a 1gig drive is easier than a 75 one...

---

### Post by quandary on 2007-12-04
It sounds like a file-system probelm...
Can you copy files on it using Windows? 

If so, it might be Linux can't write because NTFS is used.
You maybe should convert it to a FAT32 partition instead of NTFS, and also check the filesystem for errors before you do that...

---

### Post by philinux on 2007-12-04
Ok now I see your problem. This happened to me, check out lost and found and also root has a trashcan.

---

### Post by laidback on 2007-12-04
Show Hidden Files within the USB disk, you'll see a .Trash-name folder. In there are all the deleted files, to recover the space this foldeer needs to be cleared.

---

### Post by El_Matthews on 2007-12-04
Thank you all for the replays.

1. I didn't find any lost an found dir. Isn't that only for ext2 file systems? My disk is a Fat32 partition.
2. No .Trash-User or .Trash-Root have been found on the disk. Neither from win or from Linux.
3. Yes I can write to it from Windows. In fact this is my mobile disk I use on my work. I always used this disk to share date between my work and home pc (+ backup of my work pc).

I did a test with du -h and even this command sees only 65GB used. I don't understand it. Maybe there is a limit in Linux on the FAT32 filesystem?

If I do a dir (this would take all hidden files also)from dos:
5 Dir(s)   9,615,179,776 bytes free

so the problem doesn't seem to be hidden or lost files somewhere.


PS: caclratm, you're right. I don't have the 75GB free somewhere to back it up and format the disk :)


Greetings

Matthews

---

### Post by laidback on 2007-12-04
Have a look at it with Gparted and see what that reports. System>Admin..>Gnome Partition Editor. The password is your own.

---

### Post by psusi on 2007-12-04
Run a chkdsk on it from windows... the filesystem sounds like it's damaged.

---

### Post by El_Matthews on 2007-12-06
indeed a chkdsk solved the problem, thanks

---

### Post by quandary on 2007-12-21
> **El_Matthews said:**
> 
indeed a chkdsk solved the problem, thanks


Hallelujah! :lolflag:

---

