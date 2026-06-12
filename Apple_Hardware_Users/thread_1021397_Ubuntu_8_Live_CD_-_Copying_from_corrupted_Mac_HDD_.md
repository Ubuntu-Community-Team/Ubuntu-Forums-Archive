---
title: "Ubuntu 8 Live CD - Copying from corrupted Mac HDD to USB HDD"
date: 2008-12-25
forum: Apple Hardware Users
---

### Post by Skinz180189 on 2008-12-25
Hi folks,

Have tried a search but couldn't find what I was looking for.

I am using a Ubuntu 8 Live CD to try and copy some important files from a macbook pro hard drive to an external USB hard drive, before I wipe the thing and see whether the drive is salvageable (the mac boot files are fried). I have been trying to access the files in the documents area, however, I cannot open them as it says I do not have the permissions. Is there a way I can get into these files?

Another question, when copying files, I am getting a lot of input/output read errors, a sign of corrupted files?

Thanks in advance,

Gaz.

---

### Post by damis648 on 2008-12-25
First, open a terminal (Applications>Acessories>Terminal) and enter in:
```
sudo apt-get install hfsplus libhfsp0
```
and enter. It may return that it is already at the newest version, that is okay. Now enter:
```
gksudo nautilus
```
and from here you can manage your files. Good luck!

---

### Post by albinootje on 2008-12-25
> **Skinz180189 said:**
> Hi folks,

Have tried a search but couldn't find what I was looking for.

I am using a Ubuntu 8 Live CD to try and copy some important files from a macbook pro hard drive to an external USB hard drive, before I wipe the thing and see whether the drive is salvageable (the mac boot files are fried). I have been trying to access the files in the documents area, however, I cannot open them as it says I do not have the permissions. Is there a way I can get into these files?


Use sudo or gksu for that as posted by damis648.
> 
Another question, when copying files, I am getting a lot of input/output read errors, a sign of corrupted files?

Could be a sign of :
1) a messed up file-system
2) broken hard disk
3) both 1) + 2)

---

### Post by cyberdork33 on 2008-12-28
I say hard drive failing...

if you have another mac around, starting the broken machine in target disk mode and using the other mac to get access may be easier, but you can do it with the Ubuntu LiveCD.

Contrary to popular belief, you do not have to install anything to read the mac osx partition.

mount the partition from the places menu.

start two root nautilus browsers (gksudo nautilus), one pointing to the osx partition files, and the other pointing to the external hard drive. drag files to the external. You will probably need to modify permissions on the files after copying them to the external to allow user-level access.

---

