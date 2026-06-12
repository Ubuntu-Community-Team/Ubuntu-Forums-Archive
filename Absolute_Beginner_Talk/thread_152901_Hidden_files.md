---
title: "Hidden files"
date: 2006-03-30
forum: Absolute Beginner Talk
---

### Post by emptycs on 2006-03-30
How do i see hidden files? I remember pressing something and it shows all the hidden files in my home dir.

---

### Post by bluevoodoo1 on 2006-03-30
Ctrl+h

or under view "show hidden files"

---

### Post by Iandefor on 2006-03-30
For future reference, if you want to start getting into the command line a little more, you can use the command ls with the option -a to show hidden files.
```
ls -a
``` If you want to hide a file/folder, just tack a period before the rest of the name. So if you want to hide a file named ubuntu, you would rename it to .ubuntu. You can do that two ways: via the filemanager by right-clicking and clicking on "Rename", or by opening up a terminal and using the command ```
mv file .file
``` where file is the name of the file :).

---

