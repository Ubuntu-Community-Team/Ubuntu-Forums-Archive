---
title: "confusion about kernel version"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by anurag_gupta on 2006-10-01
hi
last night i did the following 
uname -a
Linux anurag-desktop 2.6.15-27-686 #1 SMP PREEMPT Sat Sep 16 02:13:27 UTC 2006 i686 GNU/Linux

everything seems to be fine but  i see "SMP" in the output but my processor is P4 2.8 ghz (i.e single core)
is this the reason for slow speed

---

### Post by petri on 2006-10-01
I get the SMP too when i try with **uname -a**

Try this instead ```
(uname -r)
``` it will give you the right version.

There is a howto for picking the right kernel at here: 
[http://ubuntuforums.org/showthread.php?t=85917&highlight=386+686+k7](http://ubuntuforums.org/showthread.php?t=85917&highlight=386+686+k7)

---

