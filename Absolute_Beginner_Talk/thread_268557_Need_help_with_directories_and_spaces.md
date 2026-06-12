---
title: "Need help with directories and spaces?"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by Matt827 on 2006-09-30
Couldn't be too discriptive in the title, but basically i want to know if there's a way to run programs from terminal that are inside of folders with a name like "world of warcraft". The space after world usually created a dead-end and the files cannot be found.

so when i run a code like this ie.
wine/hddb1/program files/world of warcraft/WoW.exe

It runs into a dead-end at the word program due to the space in the directory. I know in WIndows '%20' is the HTML markup symbol for a space. UNfortunately that doesn't work in ubuntu so is there any alternative to renaming all my directories?

wine/hddb1/program%20files/world%20of%20warcraft/WoW.exe doesn't work either so i know the windows method doesn't work :P.

Help please :D

---

### Post by divague on 2006-09-30
use quotes like this 

wine "wine/hddb1/program files/world of warcraft/WoW.exe"

---

### Post by GliderMike on 2006-09-30
Yes you can.  In brief, a backslash is used to signify a space such as /dir/world\ of\ Warcraft/.  If you have any trouble getting this input properly, the easiest way to find the right way is to use TAB completion.  It will do it for you. 

For example, type /dir/w (then hit TAB).

---

