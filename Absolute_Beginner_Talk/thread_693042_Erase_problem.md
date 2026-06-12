---
title: "Erase problem"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by Tobi-fp on 2008-02-10
Hey everybody, hope you can help me.. 
I try to erase stuff from my hard drive (its split with my windows distribution),
so, it looks as it is erased in the folder, but the size of the partition is unchanged.. I cannot see anything in the trash.. Any suggestions?

---

### Post by mikewhatever on 2008-02-10
Partitions retain their sizes regardless of whether you delete files or create them. Even a brand new partition can take, say, 10 Gb if you choose to allocate that amount of space to it.

---

### Post by Tobi-fp on 2008-02-10
The problem is that right now my partition has 9.4 gb free space of 70 gb in total. 
If i erase a file of 700 mb's the amount of free space is still the same (9.4 gb)

---

### Post by kellemes on 2008-02-10
> **Tobi-fp said:**
> The problem is that right now my partition has 9.4 gb free space of 70 gb in total. 
If i erase a file of 700 mb's the amount of free space is still the same (9.4 gb)

Probably because it's still stored in the trashcan?
Empty your trashcan.

---

### Post by Tobi-fp on 2008-02-10
Never mind, i found out.. just erased stuff from my .trash folder at /media/sda3/ folder

---

### Post by Tobi-fp on 2008-02-10
I couldnt empty it with the trash can at the desktop.. had to do it through terminal.

---

### Post by theRightNee on 2008-02-10
yeah...for future reference, when you delete things within a folder, a hidden foldder named .Trash is created, and the files are stored there (if they are not too large)...for the trashcan, i do believe it only pertains to files deleted from the desktop, or dragged into the trashcan icon. =]

---

