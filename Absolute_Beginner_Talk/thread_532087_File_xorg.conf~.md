---
title: "File xorg.conf~"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by DoricMan on 2007-08-22
Recovering from my error in xorg.conf I found this file /etc/X11/xorg.conf~ , note with a tild at the end of the filename. The file contained the previous xorg.conf data of the original file. I naturally keep a backup file copy for recovery.
Is the "tild" file usualy to be found in /etc/X11 directory, and can it be used in restoring the backup? 
Thank you.

---

### Post by milton1 on 2007-08-22
the file xorg.conf~ is a backup probably made by your editing software (gedit, kate, etc). It can be used as a backup, but I would not rely on it being always there. It may or may not be current, depending on what software you use to edit your files.

---

