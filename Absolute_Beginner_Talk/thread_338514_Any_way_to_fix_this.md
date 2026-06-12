---
title: "Any way to fix this?"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by dragonmine on 2007-01-14
Any way to remove or turn off this function.


Extraction not performed

You don't have the right permissions to extract archives in the folder "/usr/local/games/enemy-territory"

---

### Post by moshuptrail on 2007-01-14
Need a little more detail.  

Are you trying to install something?

Usually you need to use sudo to install stuff.  That looks like the problem at first blush.

---

### Post by Hendrixski on 2007-01-14
if sudoing isn't cutting it, try to chmod it.

---

### Post by dragonmine on 2007-01-14
Trying to add files to a game folder that is located in /usr/locale/games but dont have permission to acces/modify contents in the game folder.

---

### Post by moshuptrail on 2007-01-14
before you open the archive (I assume you're double-clicking on it from Nautilus)
open a Terminal and type
$ sudo nautilus
then use this nautilus to locate the archive and double-click on it
you should be able to extract the files and copy them to the desired location

---

