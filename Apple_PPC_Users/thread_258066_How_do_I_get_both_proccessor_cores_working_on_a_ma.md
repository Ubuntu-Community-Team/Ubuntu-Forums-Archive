---
title: "How do I get both proccessor cores working on a macbook pro?"
date: 2006-09-15
forum: Apple PPC Users
---

### Post by n00bWillingToLearn on 2006-09-15
How do I get both cores working on a macbook pro in Dapper?

---

### Post by rscow on 2006-09-15
You have to run the 686-SMP kernel.  Type uname -a in your terminal, and you will see what kernel you are using.

You can install the 686 kernel via Synaptic, just search for 686.

To find out how many CPU's you are using, type: ls /sys/devices/system/cpu

"if you found 2 cpu (cpu0 cpu1), smp works fine!"

I'm a noob, too, but this info I can provide.

Roger

---

### Post by stmiller on 2006-09-15
For cpu info, just do this:

$ cat /proc/cpuinfo

---

