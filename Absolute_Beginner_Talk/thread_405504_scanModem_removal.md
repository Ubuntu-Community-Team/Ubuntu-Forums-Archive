---
title: "scanModem removal"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by ss1346 on 2007-04-09
ScanModem put a locked folder with all it's files on my desktop. 
I cannot move or delete these files or folder?
Does anyone know how to delete the scanModem files.

---

### Post by RomeReactor on 2007-04-09
Hi. Open a terminal (Applications-->Accessories-->Terminal) and type

```
 sudo chmod 777 -R NAME_OF_FOLDER
```

and press enter; Then you can just delete it.

---

### Post by ss1346 on 2007-04-10
Folder deleted

Thanks for the help!

---

