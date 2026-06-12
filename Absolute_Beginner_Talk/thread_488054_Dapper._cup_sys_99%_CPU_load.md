---
title: "Dapper. cup sys 99% CPU load"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by vector on 2007-06-29
Hi all
This has pretty much always been a problem. Over a year now. Like most thinks linux I tend to just wait and the next update fixes it. However this seems to be something unique to my machine and Im not sure how to start tracking it down.

Ocasionaly and its seem to happen over night.. I hear the cpu fan ramping up and down in a Martian like Ular cry. I come in and yep the cpu is flat out. as reported by TOP

 PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
16418 jacqui    16   0 39308 8736 7120 S 97.2  0.8  13:03.03 gnome-cups-icon

cup sys is doing something real intense. This will go on for ever, well Ive left it for some hours once.

Any ideas? I normally end up kill ing it. Its not always that user and (3 on my system, wife, me,kids) they havent tried to do a print. havent left any app running that I can see would cause the problem.
We often have a number of terminals open and we just ctrl alt F# when we want to use the PC. (and were able to kick the other member off ;)  

thoughts?

mark@miranda:~$ uname -a
Linux miranda 2.6.15-28-386 #1 PREEMPT Thu May 10 09:45:43 UTC 2007 i686 GNU/Linux

---

