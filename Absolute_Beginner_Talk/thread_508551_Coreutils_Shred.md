---
title: "Coreutils Shred"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by jrandolph on 2007-07-24
Does anyone know how I can use this command on a folder 

It tells me that it is a directory every time I try to use this command on an entire folder

thanks

---

### Post by Mornedhel on 2007-07-24
There probably is a -r (as recursive) switch you have to use. But ! I have no previous experience with this command, so I'll have to ask you not to trust me, and to use the man page.

OK, I dug up a bit on shred : there is no -r switch, in fact the man page does not mention anything on directories. I suggest you get another utility : wipe, which does have a -r switch.

---

### Post by jrandolph on 2007-07-24
Does wipe allow the options that shred does 
as far as how many passes and final overwrite with zeros and
is it as secure from being recovered?

---

### Post by meatpan on 2007-07-24
Shred does not have a recursive operating mode.

One possible workaround is to use find or ls to collect a list of files recursively, and then pass the resulting list of files to the shred command.  Here is a summary, which has a lot of other useful info regarding shred: [http://www.slac.stanford.edu/comp/unix/secure-erase.html](http://www.slac.stanford.edu/comp/unix/secure-erase.html)

---

### Post by Mornedhel on 2007-07-24
The manpage for wipe :

[http://abaababa.ouvaton.org/wipe/wipe.1.html](http://abaababa.ouvaton.org/wipe/wipe.1.html)

---

### Post by jrandolph on 2007-07-24
I have installed and tried to use wipe to remove the whole folder but again it tells me I cant
anyone have any suggestions?

---

### Post by jrandolph on 2007-07-24
Bump

Anyone know how to use wipe?

---

### Post by jrandolph on 2007-07-24
This is what it is telling me

jacob@jacob:~/Desktop/misc./2$ wipe -r /folder1
/folder1: fatal: could not lstat: No such file or directory

---

### Post by Mornedhel on 2007-07-24
/folder1 is a folder at the root of your filesystem, no wonder it's not there. If your folder is in the current folder, just type wipe -r folder1 .

---

