---
title: "globally change a file type's icon"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by klep on 2007-12-01
HI, 

I've just installed Real Player and now all of my audio files have the real media icon (they dont open with real player, but they have its icon). Ive looked and cant find where to change this.

I have run:

find /usr/share/icons -mtime -2

(which i belive should show me the files modified in the past 2 days) to try and find the icons it changed so i can revert them this command doesnt show them so i dont even know where the icons to change are.


can someone pleas ehelp me here? this should be so simple but i have seen threads here and in other forums asking the same thing, never with an answer.

cheers

---

### Post by jken146 on 2007-12-01
Some icons are in /usr/share/icons and others are in /usr/share/pixmaps.  Simply widening your search might do the trick.  If you can find the icon for these files, just change it to the one you want with the same name.

---

### Post by klep on 2007-12-01
nope, not in there either.

---

### Post by klep on 2007-12-06
bump

---

### Post by CatKiller on 2007-12-06
It's not one icon that's changed, it's an entry in the MIME-type database. I don't know how any of it works, so I can't give you more than that pointer.

---

