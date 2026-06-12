---
title: "[SOLVED] Different memory usage displayed"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by Inxsible on 2007-08-01
There seems to be a discrepancy in my memory readings

The CPU monitor screenlet that I have shows Memory used 450 MB. The gnome system monitor also shows 450 MB used, but top and free below show different numbers. Am I reading it wrong?

Seems like the free and used memory are reversed in the commands free and top :(

```
inxsible@HPdv9000t:~$ free
             total       used       free     shared    buffers     cached
Mem:       2074556    1580504     494052          0     426196     684896
-/+ buffers/cache:     469412    1605144
Swap:      1004020          0    1004020
``````
inxsible@HPdv9000t:~$ top

top - 00:12:33 up 1 day,  5:27,  2 users,  load average: 0.19, 0.13, 0.13
Tasks: 131 total,   1 running, 130 sleeping,   0 stopped,   0 zombie
Cpu(s):  3.3%us,  1.5%sy,  0.0%ni, 95.0%id,  0.0%wa,  0.2%hi,  0.0%si,  0.0%st
Mem:   2074556k total,  1579820k used,   494736k free,   426328k buffers
Swap:  1004020k total,        0k used,  1004020k free,   684952k cached
```

---

### Post by Inxsible on 2007-08-01
Never mind...i just realised the used includes buffers and cached in it.

---

