---
title: "How do I change a read-only file so I can edit it?"
date: 2005-07-17
forum: Absolute Beginner Talk
---

### Post by eads1234 on 2005-07-17
How do I change a file from read-only to read-write or whatever so I can change the file? I'm using the text editor under the Applications/SysTools/Text Editor.

---

### Post by aysiu on 2005-07-17
Well, it depends.

Start by right-clicking on the file and selecting "Properties." Then, go to "Permissions" and see who has write access to the file. If only the owner does (and that's not you), you may have to temporarily become root to read this file. You can either *sudo gedit filename* or you can *sudo chmod* the file.

If this is a partition you're mounting, make sure you're mounting it with read/write access: [http://ubuntuguide.org/#automountfat](http://ubuntuguide.org/#automountfat)

Partitions that are formatted in NTFS cannot safely be written to, only read from. Hope that helps.

---

### Post by varunus on 2005-07-17
Also, if the file you're editing is a system file, only the "superuser" can edit it.  To become superuser, go to applications->run application and type "gksudo gedit" and press Run.

This will open up a gedit window that can edit every file.  But be very careful not to damage your system.  You should stick to only editing things in your home folder unless you have to.

---

### Post by eads1234 on 2005-07-17
Thanks for the help. You SOLVED my problem. I'm grateful.

---

