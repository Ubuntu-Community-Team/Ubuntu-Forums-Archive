---
title: "something weird happened"
date: 2006-06-30
forum: Absolute Beginner Talk
---

### Post by babyboss on 2006-06-30
Hello! Today, I was downloading some mp3 songs under ubuntu. After I finished my downloading, I moved them(mp3 songs) to my fat32 partition. I restarted my pc, and tried to listen to some of the songs. However, all of the mp3 songs disappeared. I couldn't find any of them under my fat32 partition. I tried to look into the fat32 partition with both ubuntu and windows xp. None of the platforms could find the songs. "show hidden file" option was enabled.
Before I moved songs to my fat32 partition, I had another folder with some words documents under that partition. Although all my songs disappeared for no reason, that folder with words documents was still there.

These are my partitions:
1 ntfs partition with windows xp system
1 ext3 partition with ubuntu
1 fat32 partition
1 ext3 partition for /home

partition cylinder is not necessary to be in the same order

anyone knows what happened?

---

### Post by woedend on 2006-06-30
did you look in the trash for both root and user just in case(hidden folders)?  Or perhaps inside the word document folder(in case you moved it inside on accident)

---

### Post by ProjectGod on 2006-06-30
something like this has also happened to me on my ext3 partition... i move files or rather save files into folders to which i have no write permission and POOF! the system says it's saved... but theyre gone!!!! sucked into a black hole!

---

### Post by babyboss on 2006-06-30
do user and root have different trash cans? if that is so, how do I open root's trash can under ubuntu?

---

### Post by woedend on 2006-06-30
yes different trashes, and normally the trash goes onto the partition it was deleted from..
from a terminal window, do -
sudo nautilus

be careful not to make any changes/move any files.  you must view hidden files.
its probably either .Trash or .Trash-root if even.  
Let me ask this...was this an old directory(ie, it was on the FAT32 partition beforehand) or one that you had just created?

---

### Post by babyboss on 2006-06-30
newly created

---

