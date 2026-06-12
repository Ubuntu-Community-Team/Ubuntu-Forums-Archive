---
title: "Deleting a folder in the Filesystem"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by Executioner on 2008-03-30
Playing around, I created a folder called "media" located in the filesystem. How do I delete this folder?

---

### Post by forrestcupp on 2008-03-30
Where at in the filesystem?  There is already a directory called media in the root directory.  You don't want to get rid of that.  I'm not going to give you instructions on how to delete that directory because that is usually where your drives are mounted.  If you made a media directory somewhere else, tell us where and we'll help you delete it.

---

### Post by kbless7 on 2008-03-30
If your absolutely sure you know what file you want to delete and don't have permissions to delete it then press <alt>F2. Then enter

```
gksudo nautilus
```

This will bring up the root file system. From there you have permissions to delete the CORRECT file. Don't delete the wrong stuff here!

---

### Post by Executioner on 2008-03-30
Thanks kbless7 that did the trick.

---

