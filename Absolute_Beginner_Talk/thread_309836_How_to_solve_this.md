---
title: "How to solve this"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by housam on 2006-11-30
After fresh installation of Dapper on a dual core laptop 2.00GHz, I applied the code: cat /proc/cpuinfo. 
I found that the cpu speed is 997.866 MHz.
How could I get the ultimate speed of the cpu.
Thanks for the help.

---

### Post by Bachstelze on 2006-11-30
You don't want to. The frequency will automagicaly increase when you'll need it to.

---

### Post by housam on 2006-11-30
Thanks , but how could I know if the 2 cores are recognized.

---

### Post by drphilngood on 2006-11-30
List  # of CPUs:

```
cat /proc/cpuinfo | grep '^processor' | wc -l
```

detailed cpu info:

```
cat /proc/cpuinfo
```

---

### Post by Bachstelze on 2006-11-30
when you do cat /proc/cpuinfo you'll have infos (freuqency, cache, etc.) for the two cores. If you don't, do

```
sudo apt-get install linux-686-smp
```

and reboot tu use the SMP kernel.

---

