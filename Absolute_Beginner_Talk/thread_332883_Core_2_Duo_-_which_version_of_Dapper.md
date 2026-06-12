---
title: "Core 2 Duo - which version of Dapper?"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by docshawnc on 2007-01-06
Hi - I just put a new processor in this machine and am currently running the 386 version of Dapper.  I'd like to take advantage of the dual processor and was wondering what I would need to do to get it running at it's best.  All comments and suggestions are greatly appreciated - thanks!

---

### Post by housam on 2007-01-06
You just have to install the smp kernel
```
sudo apt-get install linux-686-smp
```
you can see both processors after restarting
```
cat /proc/cpuinfo
```

---

### Post by docshawnc on 2007-01-06
Thanks - I wasn't sure how to look at the processors to see if it worked - good tip!

---

