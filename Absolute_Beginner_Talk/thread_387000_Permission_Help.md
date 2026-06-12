---
title: "Permission Help"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by medya on 2007-03-17
hey I have problem with permissions in ubuntu ,

I have an Encrypted Partition using Truecrypt .
Truecrypt loads it in /dev/mapper/truecrypt0
and I mount it  using this command :
sudo mount /dev/mapper/truecrypt0 /home/fred/Encdrive

every time which I mount my partition , I can just READ the files , and to delete or edit any file I have to go to Root Nautilus .

when I am in root nautilus , I try to change the permissions but they dont get changed .
for example it doesnt let me change the Group or let the "write" permission.
why is that ? how can I make my drive be mounted with like a normal folder ?


and also I have a Music folder on my FAT32 partition , everything on my fat32 Partition is Fine (I can delete copy ...blah blah) but the MUSIC folder in that partition is  READ-ONLY (I think I had made it read only in windows) I try to change the permssion using ROOT nautilus ...but it doesnt help.



I think I need a tutorial or something to learn about permissions. please guide me.

---

### Post by ahaslam on 2007-03-17
I found this helpful: [http://en.wikipedia.org/wiki/Chmod](http://en.wikipedia.org/wiki/Chmod)
But I find it easier to change premissions with MC

---

