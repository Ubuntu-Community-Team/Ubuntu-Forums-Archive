---
title: "changing permission"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by zerobinary on 2007-06-23
i can't change permission for my card reader to delete stuff in my memory card
the error is like this
Sorry, couldn't change the permissions of "Generic STORAGE DEVICE".
and 
Couldn't change the permissions of "Memory card" because it is on a read-only disk
You do not have permissions to write to this folder.

---

### Post by DrRootabega on 2007-06-23
how are you trying to modify the permissions.  Try using the mount point, whatever that is for you.  Also, use sudo chmod instead.
If you don't want to use the terminal, use 

sudo nautilus

and change the folder permissions using that (remember to modify permissions recursively.)

---

### Post by zerobinary on 2007-06-23
but i have another problem now
Error "Invalid parameters" while copying "/home/zerob.../hacksign ".
can't copy that files to my mini sd

---

### Post by starcraft.man on 2007-06-26
> **zerobinary said:**
> but i have another problem now
Error "Invalid parameters" while copying "/home/zerob.../hacksign ".
can't copy that files to my mini sd

Hi there Zero. Been busy. Now lets see if I can help. First off, basic questions... Whats the file system on the stick/card? If its NTFS, you need the drivers don't forget that. Were you using CLI to edit the permissions, if so, what command did you issue?

As for the copy problem, what was the command you used (I assume it was cp from the terminal...), paste it here and we can try and correct it (if its not obvious, be sure to say what you want to do with it).

General answers to these problems:

[Modfying permissions from CLI]("http://www.linuxcommand.org/lts0070.php")
[CP command and wild cards]("http://www.linuxcommand.org/lts0050.php")

Any questions, feel free to post again.

---

