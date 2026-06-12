---
title: "Overclocking issues"
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by brotakul on 2006-08-13
[SIZE="2"][B]my sistem: 
AMD 64 2800+ 
EPoX 8kda3i, sk754
512 DDR400 Kingmax[/B][/SIZE]

**OS: Ubuntu 6.06**

I overclocked my CPU using some stable settings which I already test them under Windows [dual boot]. The *CPU Frequency Monitor* applet error appears:

```
CPU Frequency Scaling Unsupported - You will not be able to modify the frequency of your machine. Your machine may be misconfigured or not have hardware support for CPU frequency scaling.
```

```
brotakul@brotakul:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 4
model name      : AMD Athlon(tm) 64 Processor 2800+
stepping        : 10
cpu MHz         : 2340.046
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext lm 3dnowext 3dnow
bogomips        : 4684.87

```

Please tell me what to do because I searched the WEB and this Forum, I found some similar problems, but I am a bigineer and I don't want to do it by myself and mess up my installation again. I already reinstalled Ubuntu 4 times in one month :(.

---

### Post by brotakul on 2006-08-14
up.

noone knows how to solve this?

---

### Post by yohanseh on 2006-09-03
you must configure a custom kernel, at least that is how i got it to work

---

