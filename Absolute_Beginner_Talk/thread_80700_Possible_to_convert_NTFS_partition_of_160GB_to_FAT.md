---
title: "Possible to convert NTFS partition of 160GB to FAT32 (file Max 2GB)?"
date: 2005-10-22
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2005-10-22
Hi, 

Sorry for this damn newbie question : Is it Possible to convert NTFS partition of 160GB to FAT32 (file Max size of 2GB (one zip file))  ? 
 
 
I could u use partition magic or qtparted from knoppix ?
  
Thank u very much for ur wise reply, 

With my best regards, 

Patrick

---

### Post by patrick295767 on 2005-10-22
(this is solution to make a backup of the 160 GB, then reformatting to EXT3)
  
(Linux user happy)

By the way, is there some programs dedicated to make backup of harddisk in linux (just inserting dvd's or cd's ... then ok  and so on)?

thank you very much !!

---

### Post by aysiu on 2005-10-22
It depends on what you mean by "convert." You cannot keep your data on there and just change the filesystem. If you "convert" an NTFS partition to a FAT one, you're essentially erasing (reformatting) your NTFS and then creating a FAT one--all data will be lost.

---

### Post by nitricacid on 2005-10-22
You can't convert NTFS to FAT32 without loseing data.
You also can't install a FAT32 WinXP on a harddisk that has more then  (i think) 80gigs unless you use a previous version (Like Win95\98 ).
-----


BTW I like your Adventure Game Icon.
Could that be from 'Lure of the Temptress' ??

---

### Post by blastus on 2005-10-23
The maximum FAT32 size is very large. However, with XP, you cannot create a FAT32 partition that is larger than 32 Gb. The reason is that the cluster size would jump to 32K, making the file system very inefficient. However, manufacturers who preinstall XP on machines can create FAT32 partitions larger than 32 Gb. 

If I were you I would reorganize your data such that you can burn it off on CDs. I would only use FAT32 for sharing data between Linux and Windows, otherwise store all your data on NTFS (if you need Windows) or ext3 for Linux. FAT32 is not a journaled file system and is not recommended for storing any kind of data on it for any purpose other than temporarily sharing data between Linux and Windows.

---

### Post by patrick295767 on 2005-10-23
[QUOTE=blastus]The maximum FAT32 size is very large. However, with XP, you cannot create a FAT32 partition that is larger than 32 Gb. The reason is that the cluster size would jump to 32K, making the file system very inefficient. However, manufacturers who preinstall XP on machines can create FAT32 partitions larger than 32 Gb. 

If I were you I would reorganize your data such that you can burn it off on CDs. I would only use FAT32 for sharing data between Linux and Windows, otherwise store all your data on NTFS (if you need Windows) or ext3 for Linux. FAT32 is not a journaled file system and is not recommended for storing any kind of data on it for any purpose other than temporarily sharing data between Linux and Windows.[/QUOTE]
  
First of all, thank you for your reply !!
Then, it's what I guessed... I'll have to make backup of my big harddisk of 160GB... I bought some DVD in order to do so... 
So, now, i'll have to look for a linux program that makes backup rather automatically or copy of my harddisk. Then, i'll use windows total commander (with wine) and a plugin to store virtual tree of my burnt DVD (lst files that u can search into it ... 
 
I'll have fun !
Thank you !
If you have any clues to help my tasks, please do not hesitate to let me know !!
  
Patrick 
[email]Patrick295767@hotmail.com[/email]

---

### Post by hubbadub on 2005-10-23
I used Norton PartitionMagic or whatever the norton systemworks one is called, in windows XP, to convert my 80gb ntfs drive to fat32. It did this in about 15 minutes, with no apparent errors. Im using files off the drive in Ubu as we speak. The process could not have been more seamless.

---

