---
title: "Ram"
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by drito on 2006-12-13
Since I have installed Beryl 0.1.3 I have some problems with RAM usage. Is Beryl responsible for this? Here is snapshot from System Guard.

---

### Post by BarfBag on 2006-12-13
It's possible.  One of the reasons I stopped using Beryl is because of how much power it hogs.  ](*,)

---

### Post by dmartinsca on 2006-12-13
What's wrong with the ram usage? The blue is actually used memory, the yellow and orange are buffers and cache, they can be freed up very quickly if a new program is loaded or something suddenly requires more memory. 

Linux takes a different approach to memory usage than windows does. The basic idea is, why not keep data which was loaded from hard disk at some point and is no longer needed in memory in case it is needed again, and if something else needs that space then we'll just have to get out of the way!

You can get an idea of how much memory is actually used, and what is available for new programs by running **free -m** in a console

```
dmartins@dmartins-laptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1001        987         14          0         61        467
-/+ buffers/cache:        458        543
Swap:         1027         17       1010
```

The line starting with "-/+ buffers/cache" shows the amount of memory used minus the buffers and cache, this is probably much more like the amount of free/used memory that windows would display.

Ah, here is the explanation I was looking for: [http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)

---

### Post by drito on 2006-12-13
I knew I should post snapshot :) Thanks a lot!!!

---

