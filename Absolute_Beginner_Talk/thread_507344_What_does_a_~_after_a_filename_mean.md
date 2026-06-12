---
title: "What does a ~ after a filename mean?"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by woodsonoversoul on 2007-07-22
been editing files with gedit and now files that I've closed and come back to the next day have a tildy(sp) at the end. It also doesn't look like I'm saving them...

---

### Post by yabbadabbadont on 2007-07-22
Gedit appears to be configured to make a backup copy of the file every time you save.  The ~ at the end is just the name of the backup.

---

### Post by woodsonoversoul on 2007-07-22
What's the deal with it acting like it's not saving the changes I've made when I reopen these files? Also, When I just type the regular filename it brings up the "backup", the one with the ~ at the end...

---

### Post by be4truth on 2007-07-22
Are you sure you have write permissions? For many configuration files you need to have super user write permissions. Instead of 'gedit filename' try 'sudo gedit filename' but be careful as you acted as the administrator in this case and can damage your system. You should make in any case always a backup copy before you edit a file. Type cp /path/to/the/file/filename /path/to/the/file/filename.backup

---

### Post by woodsonoversoul on 2007-07-22
Thanks be4truth and yabbadabba, That sorted it out!

---

### Post by steveneddy on 2007-07-22
> **yabbadabbadont said:**
> Gedit appears to be configured to make a backup copy of the file every time you save.  The ~ at the end is just the name of the backup.

Isn't he so smart?

---

