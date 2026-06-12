---
title: "Monitor cpu from commandline"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by pompiuses on 2006-10-07
How can I monitor cpu and memory usage from the commandline?

I tried to do a search on 'cpu', but search seems to have problems right now since it came up with zero hits :confused:.

---

### Post by mcrae on 2006-10-07
try top

---

### Post by highneko on 2006-10-07
top
Edit: Damn, someone beat me.

---

### Post by codejunkie on 2006-10-07
> **pompiuses said:**
> How can I monitor cpu and memory usage from the commandline?

I tried to do a search on 'cpu', but search seems to have problems right now since it came up with zero hits :confused:.

```
top
``` gives the currnet running processes cpu usage memory usage 
```
cat /proc/cpuinfo
``` gives cpu speed modle type etc,
```
acpi -V
``` gives cpu temp if you motherboard supports temp monitoring this may or may not be avaliable for you.
```
free
``` also monitors memory and swap file usage

hope these help.

---

### Post by highneko on 2006-10-07
> **codejunkie said:**
> 
```
free
``` also monitors memory and swap file usage

This's my output for free;
```
highneko@ubuntu:~$ free
                      total       used       free     shared    buffers     cached
Mem:       1027268     536048     491220          0      58692     252004
-/+ buffers/cache:     225352      801916
Swap:      2096472          0       2096472
highneko@ubuntu:~$
```

Is that good or bad?

Does this forum have a fixed width font? This's looking bad!

---

### Post by pompiuses on 2006-10-07
Thanks guys :)

---

### Post by codejunkie on 2006-10-07
> **highneko said:**
> This's my output for free;
```
highneko@ubuntu:~$ free
                      total       used       free     shared    buffers     cached
Mem:       1027268     536048     491220          0      58692     252004
-/+ buffers/cache:     225352      801916
Swap:      2096472          0       2096472
highneko@ubuntu:~$
```

Is that good or bad?

Does this forum have a fixed width font? This's looking bad!

that doesn't seem bad, linux appears to use a little more ram than windows xp seems to, the key word seems because linux caches things into ram for faster execution and when something else needs/requests that memory it frees the memory for that application to use, unlike winxp which seems to keep memory acclocated for an applictaion even after that application is closed, i hope i made some sence there but that does seem ok so i wouldn't worry about it.

---

