---
title: "NTFS cp ext3"
date: 2006-05-05
forum: Absolute Beginner Talk
---

### Post by GaFFy on 2006-05-05
How come I can read my NTFS drive files but I cant copy them to my desktop.
I can open an xls into open office just fine, but I need to copy a complete folder and it says:

gaffy@gafserv:~$ sudo cp /windows/ /home/gaffy/Desktop/Backup/
cp: omitting directory `/windows/'

Is there a way to copy entire ntfs folders to the desktop?

---

### Post by hw-tph on 2006-05-05
**cp -R** for recursive (include directories and subdirectories). This applies to all filesystems.


Håkan

---

### Post by GaFFy on 2006-05-05
<slap forehead> duh :rolleyes:

---

