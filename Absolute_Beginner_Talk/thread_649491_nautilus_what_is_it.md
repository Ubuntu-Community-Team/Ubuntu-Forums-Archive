---
title: "nautilus what is it"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by twist2b on 2007-12-25
VERY VERY newbish question.
i dont understand it so how do you use it.... cause i need to open it or somerthing like to install fonts.... heres the guide:

To install fonts, as root, open nautilus window and type "fonts:///" in the location bar. Now copy
all the .ttf files there which are included in the archives (.tar.gz files etc.) in Fonts folder. Open
a terminal window and type: "fc-cache -f -v". Restart and you can now use OSX fonts.



so how do i open it?

---

### Post by PmDematagoda on 2007-12-25
Nautilus is the file manager for GNOME like Windows Explorer is for Windows. You can open Nautilus simply by double-clicking on a folder or by executing:-
```
nautilus
```

---

### Post by lamalex on 2007-12-25
nautilus is the gnome file manager, to open it as root, open a terminal or hit alt+f2 and type ```
gksudo nautilus
``` then do what the instructions say.

---

### Post by oldos2er on 2007-12-25
To open nautilus as root, open a terminal and type "gksudo nautilus".

---

