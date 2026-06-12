---
title: "[SOLVED] Is there a software for creating ntfs partions?"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by bhadotia on 2008-04-12
So is there any such software guys? I've got Gparted but it cannot create ntfs?

---

### Post by LaRoza on 2008-04-12
There is another package I think that GParted uses for making NTFS.

The live CD has it, but I do not know its name. 

But it doesn't work well with Windows, from what I heard. It is best to use Windows to do the NTFS formatting.

---

### Post by jeffus_il on 2008-04-12
Install ntfsprogs:
```
sudo apt-get install ntfsprogs
```gives you a program mkfs.ntfs which I think gparted will pick up.
( You may also be better off using fat32 as a medium which both Linux and Windows can read.)

---

### Post by ibutho on 2008-04-12
To access the ntfs partitions, also install ntfs-3g if its not already installed.

---

### Post by bhadotia on 2008-04-12
Does ntfsprogs have a gui? I want a software with a gui I'm yet not comfortable with terminal.

---

### Post by bhadotia on 2008-04-12
Alright, I get it Gparted picks it up; now we can create ntfs partions from the partion editor itself.


THanks GUys!

---

