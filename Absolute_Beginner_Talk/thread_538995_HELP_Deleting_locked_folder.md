---
title: "HELP Deleting locked folder"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by Oro_07 on 2007-08-30
I cannot delete this locked folder on my desktop?  Can someone help me delete this folder..

---

### Post by annda on 2007-08-30
i suggest ALT+F2 
```
gksudo nautilus
```

this will launch a file manager with root privileges (something like super admin) and you will be able to delete it. however, the folder will still be in your root trash.

you can do that in the terminal too to remove it completely:

```
sudo rm -R ~/Desktop/name_of_folder
```

---

