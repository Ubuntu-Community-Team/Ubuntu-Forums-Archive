---
title: "How to remove files of a certain type in a folder/all subfolders?"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by steven_mckenz on 2007-01-16
I copied all of my music from one of my harddrives on Windows to a HDD on my Ubuntu system.  Unfortunately, this also copied over all of the thumb.db, and album_art.jpg files over that Windows Media Player had created when I imported all the CDs way back when.

I have a lot of music, and I really don't want to go through the folders one by one to remove all the miscellaneous materials out of the folders.  So my question is, is there some sort of command that I can use in the terminal to have Ubuntu delete all of a certain filetype, so I can get rid of all of that miscellaneous "junk" out of the folders?

Thanks!

---

### Post by nsleiman on 2007-01-16
simply do a "find" and delete the results :)

---

### Post by dann0 on 2007-01-16
Remove files: **rm FileName**

To find all Thumbs.db in current folder, and in all subfolders:
**find ./ -name 'Thumbs.db'**

Removing all Thumbs.db from subfolders:
**rm `find ./ -name 'Thumbs.db'`**

See also **man rm** and **man find**

---

