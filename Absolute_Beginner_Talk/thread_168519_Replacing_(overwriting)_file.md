---
title: "Replacing (overwriting) file"
date: 2006-04-30
forum: Absolute Beginner Talk
---

### Post by ZBREAKER on 2006-04-30
I am truly brainwashed by Windows. Am trying just to replace one file by another thru drag and drop, but Ubuntu tells me I'm not the owner of the folder and cannot do this. Quick help for a noob?

---

### Post by Rinzwind on 2006-04-30
If you are not the owner you can do the moveing as root but you'd end up with the same problem next time.

Best way is to change the rights of the file. Go into a terminal session and go to your file. If you type:

sudo chmod {yourusername} {yourfilename}

you should remove the lock and will be able to overwrite the file.


How did you create the file you have now? Cuz you probably did that with another user and Linux is very picky (and rightly so!) about who owns a file and what others can do with it.

---

### Post by aysiu on 2006-04-30
Press Alt-F2.

If you're using Gnome, type ```
gksudo nautilus
```
If you're using KDE, type ```
kdesu konqueror
```

---

