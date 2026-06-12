---
title: "How Do I Drag-and-Drop When I Don't Have Permission?"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by stropyboy11 on 2008-03-04
I'm trying to drag and drop the file for flashplayer into the Opera file to enable flash player in the Opera browser. I copied the file (libflashplayer.so) to the desktop, and then dragged it to the appropriate file, but it says I don't have permission....what do I do????

---

### Post by stropyboy11 on 2008-03-04
I'm trying to drag and drop the file for flashplayer into the Opera file to enable flash player in the Opera browser. I copied the file (libflashplayer.so) to the desktop, and then dragged it to the appropriate file, but it says I don't have permission....what do I do????

---

### Post by amazingtaters on 2008-03-04
do this in the terminal

```

cd Desktop
sudo mv libflashplayer.so "destination folder"

```

---

### Post by Crooksey on 2008-03-04
```

$ sudo nautaulis --no-desktop
```

Run the file manager as root :-)

---

### Post by iris-n on 2008-03-04
open your terminal, and type ```
gksu nautilus
``` This will open a privileged session of the file browser and you will be able to do it.

---

### Post by stropyboy11 on 2008-03-04
Do I run it all as one command or two seperate ones?

---

### Post by aysiu on 2008-03-04
> **Crooksey said:**
> ```

$ sudo nautaulis --no-desktop
```

Run the file manager as root :-)
It should be Alt-F2 ```
gksudo nautilus
``` instead of *sudo nautilus*

---

### Post by kellemes on 2008-03-04
Or start your filemanager with root privileges like so..
```
gksudo nautilus
```
Now you can drag-drop without issues.

---

