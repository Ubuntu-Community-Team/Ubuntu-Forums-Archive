---
title: "mount jungle disk share"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by stevieb on 2006-09-17
hello,

i'm trying to mount my jungle disk share so i can access it as part of my file system.  this is the command i'm supposed to use:```
mount.davfs http://localhost:2667 /mnt/MOUNTPOINT -o nolocks
```

i don't know what to plug in instead of "MOUNTPOINT."  I want the folder to show up on the desktop.

thanks for answering another stupid noob question,

-steve

---

### Post by raldz on 2006-09-17
that's not a stupid question..

Create a new folder first in your desktop and give a name for it like example: REMOTE_FILES

then try to replace your "/mnt/MOUNTPOINT" with 
"/home/<your username>/Desktop/REMOTE_FILES"

you may want to change the icon of the folder if you like..

---

