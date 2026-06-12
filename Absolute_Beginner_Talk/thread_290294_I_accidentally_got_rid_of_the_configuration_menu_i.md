---
title: "I accidentally got rid of the configuration menu in KDE"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by Amablue on 2006-11-01
You know, the menu that appears under "actions." Its the one that leads to the menu that lets me add and remove that stuff. ](*,) 

I've effectively locked myself out of my own house.

---

### Post by Arevos on 2006-11-01
I no longer use KDE on my system, but IIRC any menu alterations carried out by a user are stored in "~/.kde/share/applnk". If we move this directory to a a backup location, then the next time KDE starts up, the menu should have reset back to the system default. To do this, open up a terminal (konsole) and type:
```
mv ~/.kde/share/applnk ~/applnk-backup
```This should successfully undo any changes you have made. In case something goes wrong, you should be able to revert back to the original state with:
```
rmdir ~/.kde/share/applnk && mv ~/applnk-backup ~/.kde/share/applnk
```

---

