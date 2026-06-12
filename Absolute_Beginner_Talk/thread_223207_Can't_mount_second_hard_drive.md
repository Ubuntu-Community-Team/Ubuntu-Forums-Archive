---
title: "Can't mount second hard drive"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by navymom on 2006-07-26
I have two hard drives on my computer.  One is mainly for storage.  I can see it when I click on the Computer icon but when I try to access it I get an error telling me that it can't be mounted because it isn't removable.  I have almost 10 gigs of songs, videos, pics, and back up files on it.  I'd really like to be able to access my music.  Thanks.

---

### Post by moma on 2006-07-26
Hello,

Can you provide some details of your harddisks. Reply and paste output of these commands:

$ sudo fdisk -l 

$ cat /etc/fstab 

What partition do you want to mount?
What is the type of file system (ext3, NTFS, fat32)?
How do you mount?

---

### Post by navymom on 2006-07-26
Well...I kinda just double click on it and it tells me that it can't mount it. So, I guess my method of mounting is double-clicking. lol

---

### Post by navymom on 2006-07-26
I can't tell you what the specs are by the code without rebooting to Ubuntu, but I do know that it's FAT32 if that helps.

---

### Post by kurniawands on 2006-07-26
yes, do what moma said... or go to system > administration > disks, and see what you got.

in case of you have it on ntfs, you can try use ntfs-3g, "how to" page can be found [here]("http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g").

i think moma has the link for fat32 disk mounting thing.. i've seen some where else... :-k

---

### Post by kurniawands on 2006-07-26
ha... found that link... here it is [http://easylinux.info/wiki/Ubuntu_dapper](http://easylinux.info/wiki/Ubuntu_dapper) and said to look for the 15th chapter...:-D

---

### Post by navymom on 2006-07-26
ty ty ty!!!  will print it and try it out in a bit!

---

