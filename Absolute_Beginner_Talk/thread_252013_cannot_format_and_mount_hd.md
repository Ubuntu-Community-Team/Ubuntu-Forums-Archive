---
title: "cannot format and mount hd"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by rumi on 2006-09-06
Hi evrybody, i'm tring to format and mount the second hd where at the moment I have a win os installed. what i want to do is just format the win sistem and make the hdb ready to be used from ubu, I tried with gparted and did not make it, it seams that the previous ntfs format can not be erased. And also fstab seams to be not properly set, anyone can give me a help.:-| 
Ciao!
(sorry for bad english)

---

### Post by rumi on 2006-09-06
[QUOTE=rumi;1468994]Hi evrybody, i'm tring to format and mount the second hd where at the moment I have a win os installed. what i want to do is just format the win sistem and make the hdb ready to be used from ubu, I tried with gparted and did not make it, it seams that the previous ntfs format can not be erased. And also fstab seams to be not properly set, anyone can give me a help.:-| 
Ciao!
(sorry for bad english)

---

### Post by benfindlay on 2006-09-06
Ok, this solution is cheating ;) but you could just put your windows xp install disk and reformat the drive as FAT32. Then you shouldn't have any problems using the drive or reformatting it to ext3/reiserFS/whataver format you want to use

---

### Post by anaconda on 2006-09-06
gparted should work.. if it is run as root and the windows-drive isn't mounted..

yep. windows CD would definitely work..

cfdisk from terminal should also work.
sudo cfdisk /dev/hda   (or hdb)

---

