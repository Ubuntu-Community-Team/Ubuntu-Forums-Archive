---
title: "ram usage"
date: 2005-06-29
forum: Absolute Beginner Talk
---

### Post by bassMonkey on 2005-06-29
Hi,
simple question: can anyone explain to me why my ubuntu-system uses this much ram: > top - 14:36:46 up  5:16,  2 users,  load average: 0.31, 0.25, 0.20
Tasks:  79 total,   2 running,  77 sleeping,   0 stopped,   0 zombie
Cpu(s):  6.7% us,  0.7% sy,  0.0% ni, 92.3% id,  0.0% wa,  0.3% hi,  0.0% si
Mem:    516344k total,   386708k used,   129636k free,    12796k buffers
Swap:   979956k total,     2888k used,   977068k free,   208136k cached
 

but according to "system monitor" It only uses 164.1MB (isn't that alot too?)...

---

### Post by doclivingston on 2005-06-29
According to the output your machine is using around 376Mb of ram, and ~2.5Mb of swap memory. However of that memory, 203Mb is "cached", which means that it is simply being  used as a copy of something on disk (it's not actually being "used" by any programs); and 12Mb is being used by "buffers", to load/save something to disk.

(Ram + Swap - Cache - Buffers) is basically the formula that the system monitor uses to determine how much memory is in use. It's better to have you machine use some memory to store a copy of something on disk, rather than have it sit there doing nothing (Linux tends to be a bit better at this than Windows). Whether 165Mb is a lot, or not, really depends on what programs you have running, and what you've been doing in them. As long as the amount of swap memory being used doesn't get too big, you shouldn't have any problems.

---

### Post by az on 2005-06-29
Memory is useless unless you use it.  The more your system caches, the faster your system will be.

---

