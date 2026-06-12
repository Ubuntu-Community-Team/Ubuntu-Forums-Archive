---
title: "External Drive Icon Stuck to Desktop..."
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by Dusibello on 2006-11-22
thanks for taking the time to read this, and a deep bow from the knee in tearful gratitude for this MARVELOUS os....

have attached a WD 'MyBook' external USB drive, and that is happy, too. and i like how DD puts a drive icon on the desktop - pretty nifty...

however, am trying to live with a clean, <obsessively> tidy, icon-free desktop.... have succeeded in dragging/dropping the MyBook drive launcher icon to the 'Places' menu, but can only copy it there, where i want to actually **move** it off the desktop... nor can i find a way to delete the launcher icon from the desktop after it has been copied to the Places menu... (after trying dragging with ctrl, alt, shift, etc.)

would be grateful for a kick in the right direction - cheers.

---

### Post by CatKiller on 2006-11-22
**gconf-editor**
/apps/nautilus/desktop/volumes_visible

---

### Post by Dusibello on 2006-11-22
cheers.

translation for any future noobs that may have found this thread via search and, like me, stared at catkiller's answer like a clueless caveman :rolleyes:  :

open a terminal session
type: gconf-editor
browse down the tree and uncheck the volumes-visible setting

---

