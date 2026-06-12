---
title: "Quadcore but only one core in system monitor.."
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by Keddy on 2008-01-06
Hi there, 
I just installed Gutsy. I installed Maya 64bit edition..everything is smooth..But its slow. When i checked sytem monitor, it seems there is only one core active. CPU 0. Wherre is the other 1,2 and 3 :P 
My kernel seems default but not smp. What's the easiest way to run smp kernel ?

---

### Post by blueridgedog on 2008-01-06
Are you certain that it only "sees" one core?  Try:

```
 cat /proc/cpuinfo
```

I was under the impression that the current generic kernel in Ubuntu supported SMP.

---

