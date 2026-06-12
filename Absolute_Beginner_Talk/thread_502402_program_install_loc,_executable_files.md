---
title: "program install loc, executable files?"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by kefurd06 on 2007-07-16
should be an easy answer for ppl versed in linux. i'm a windows vet so some of this stuff is a bit strange to me. 

1 what are the executable files' extensions? 
2 where can i find software installations? (i ask because i want to change the program that opens streaming net radio but i don't know where to find that program and it's not in the initial list)

thanks :D

---

### Post by yabbadabbadont on 2007-07-16
1) There are no "extensions" for executable fils in Unix/Linux.  The file *permissions* decide if it can be executed.

2) Run System->Administration->Synaptic Package Manager.  Browse around the sound related categories to see if anything catches your fancy.

---

### Post by dmorand on 2007-07-16
I believe the programs should be in /usr/bin folder.

---

### Post by yabbadabbadont on 2007-07-16
> **dmorand said:**
> I believe the programs should be in /usr/bin folder.

Programs can reside anywhere in the filesystem.  /usr/bin is just the directory normally used.  :D

---

### Post by kefurd06 on 2007-07-16
thansk for the help guys. usr/bin was there it was at (totem)

---

### Post by yabbadabbadont on 2007-07-16
By the way, I found a good explanation of the Linux file permissions here:

[http://www.freeos.com/articles/3127/](http://www.freeos.com/articles/3127/)

---

### Post by pbaehr on 2007-07-16
Just to clarify the extension point:

In Windows three letter extensions are used by the OS to determine the type of file. If you change the extension, for example .exe to .prg, Windows doesn't know what to do with it.

In Linux, extensions are based on naming conventions, but are not necessary to the OS. If you rename your .txt file to .abc it won't hurt a bit. They can even be done away with completely with no negative effect. Really, they're just there for your sake so you can quickly know what's in a .txt file.

---

### Post by dmorand on 2007-07-16
Very good explanation!

---

