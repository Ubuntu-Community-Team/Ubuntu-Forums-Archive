---
title: "Memory Upgrade problems"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by aam-aadmi on 2007-04-16
I have two memory slots in my Dell Dimension 3000. Each had a 256 MB RAM. I recently replaced one of them with a 1GB RAM. But, the system does not seem to have the correct total memory. This is what I get
[HTML]basu15@cpe-24-33-76-208:~$ free
             total       used       free     shared    buffers     cached
Mem:       1034572     365084     669488          0       7508     170516
-/+ buffers/cache:     187060     847512
Swap:      1510068          0    1510068
[/HTML]

Why is the total 1034572 and not 1284000 (1028 + 256)? Do I need to configure the system or some such thing?

---

### Post by mand0 on 2007-04-16
If I am not mistaken I believe what your computer is telling you is correct.  There is a difference between 'normal' numbers and [binary numbers]("http://en.wikipedia.org/wiki/Binary_numeral_system").

---

### Post by aam-aadmi on 2007-04-16
I am a little confused because my laptop (with 1GB RAM) shows the following:
[HTML]basu15@basu15-laptop:~$ free
             total       used       free     shared    buffers     cached
Mem:       1026836     370352     656484          0      12908     198360
-/+ buffers/cache:     159084     867752
Swap:      2168732          0    2168732
[/HTML]

This is not very different from what my desktop is showing where I have just installed a 1GB memory and which already had a 256MB RAM.

---

