---
title: "can't uninstall game that i installed with wine!"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by axemurder785 on 2007-08-06
help! i installed harry potter and the sorcerers stone with wine (or at least i think i did :( ) and it dosen't work and i want to uninstall it somehow. could someone help me see if i've installed it at all, and if i did could you tell me how to delete it?

---

### Post by xopher_mc on 2007-08-06
All the wine files are in 

/home/username/.wine/

you should find you files somewhere in there if you installed it.

---

### Post by be4truth on 2007-08-06
If you work on KDE-desktop check in the folder lost and found in the startup menue. If you use Gnome goto APPLICATIONS/WINE/.........
If that is the only application you run on wine you can purge wine 
Type in a terminal:

```
sudo apt-get remove --purge wine
```

then reinstall wine.

---

### Post by BangBang on 2007-08-06
try typing in the terminal

wine uninstaller

or go to your home folder, press ctrl+h to show hidden files then go to 
.wine/drive_c/Program Files to see if it actually installed.

---

### Post by axemurder785 on 2007-08-06
this issue is now resolved by using "sudo wine uninstaller" in the terminal!!!! :guitar:

---

### Post by Gremlinzzz on 2007-08-06
> **axemurder785 said:**
> help! i installed harry potter and the sorcerers stone with wine (or at least i think i did :( ) and it dosen't work and i want to uninstall it somehow. could someone help me see if i've installed it at all, and if i did could you tell me how to delete it?

If you want to delete the potter folder use the command
gksudo nautilus
then find the folder and delete it
:guitar:

---

### Post by por100pre1 on 2007-08-06
**This is the actual command:**

```
uninstaller
```

---

