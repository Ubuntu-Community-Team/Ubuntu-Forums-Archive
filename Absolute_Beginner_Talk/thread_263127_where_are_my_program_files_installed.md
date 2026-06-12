---
title: "where are my program files installed?"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by jjf on 2006-09-22
I installed a typing game called typespeed.  The object is to type words as fast as possible before they can scroll all the way across the screen.  I imagine that those words are stored in a text file somewhere.  I want to be able to edit that text file and put in whatever words I want.

Problem is I don't know where to find any program-related files.  Neither Beagle nor gnome-search-tool could find any file called "typespeed" (which is the command I type to launch the program).  So I either need to know where program files are likely to reside, or at least how the OS is recognizing "typespeed" and launching the appropriate program (so I can see what file it is launching).

Thanks.

---

### Post by zxee on 2006-09-22
> whereis typespeedshould give you the executable and other typespeed files-which are usually located in /usr

---

### Post by lamego on 2006-09-22
If you installed it from a .deb package you can list all the files installed from that package with:
```
dpkg -L package_name
```

---

### Post by SunnyRabbiera on 2006-09-22
usually programs in linux are directed to usr/bin or usr/lib debending.
most of the time programs are directed to usr/bin but depending on the program its located in usr/lib, for example firefox usually has a symbolic link in usr/bin but the program itself is in usr/lib.

---

