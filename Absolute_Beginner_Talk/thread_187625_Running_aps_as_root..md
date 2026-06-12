---
title: "Running aps as root."
date: 2006-06-03
forum: Absolute Beginner Talk
---

### Post by someusernoob on 2006-06-03
First: 
Disk 1 NTFS (windows)
Disk 2 Ubuntu (6.06 LTS)
Disk 3 FAT32 (for exchanging data between the two)

!! I know that Linux can read/write to FAT32 and ONLY read NTFS.

When i log in as user, i can acces my Ubuntu and FAT32 disk, however, im not allowed to change any files on the FAT32 disk. I can not access my NTFS disk at all (no permissions).

When i log in as root, i can acces and change my FAT32 disk and content. And i can just acces my NTFS disk and copy files to the other disks. (I cant change permissions)

So i have a couple of questions:

1. Why does only the root have the most possible access to the disks? 
2. I can run sudo nautilus for changing files (FAT32) and acces to the NTFS disk when im logged in as user, and for my music (its on the NTFS disk) i can run sudo banshee (my music player), so i dont have to copy my music to the FAT32 disk to read it, but is running these aps (especially banshee) as root dangerous/less secure?
3. I have some experience with an older Dapper Drake (unstable) release, and what i remember is that i could just acces and read my NTFS disk as a user, and also read/write to the FAT32 disk. Did they change anything? (It's a couple of months ago now)
4. Or did i just overlook a stupid setting somewhere that im not aware of yet.

Everything just runs fine, only those things are my "worries". 

Thanx for reading, hopefully you can answer my questions.

---

### Post by steve.horsley on 2006-06-03
[http://www.krazypenguin.net/Ubuntu_Dapper_Drake_6.06_Guide#Windows](http://www.krazypenguin.net/Ubuntu_Dapper_Drake_6.06_Guide#Windows)

---

### Post by someusernoob on 2006-06-03
Many many thanx. I now automount them at boot, and can access them rightaway like i was used to.

No further questions untill now.

:p

---

