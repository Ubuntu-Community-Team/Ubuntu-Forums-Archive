---
title: "How do I change owner of multiple files/folders"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by randiroo76073 on 2006-12-05
I need to change owner of multiple files/folders[icons] inside of my home/username folder, I "gksu nautilus" and changed the folder but all contents[1573} are still root, is there a command that will change them all at one time?

---

### Post by compmodder26 on 2006-12-05
you can do

```
sudo chown -R username_of_new_owner foldername 
```

That will change ownership of every file in the folder.  It will even do so in subfolders too.

---

### Post by randiroo76073 on 2006-12-05
Thanks compmodder, still learning all commands :)

---

### Post by abuakel on 2008-04-27
Thank you

---

