---
title: "Change permition to folder (and all folders and files, in that folder)"
date: 2006-04-21
forum: Absolute Beginner Talk
---

### Post by aktiwers on 2006-04-21
How do I change the permition to a folder, so all the folders and files in that folder will get the exact same permition?

I have a folder with 60gb of files and folders, and I would like them all to be the same permition.

Thanks for any help

EDIT:
I want all users to be able to read/execute.

Thanks again.

---

### Post by taurus on 2006-04-21
From a terminal, type
```

sudo chmod -R 755 folder_name

```

---

### Post by Qrk on 2006-04-21
```
sudo chmod -R u=rwx,g=rx,o=rx /path/to/directory/
```

---

