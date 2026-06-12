---
title: "Is my dual core detected? cpuinfo output attached"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by englishaugust on 2007-04-05
Hi all, 

Just wondering if my dual core is detected, i did 
[HTML]cat /proc/cpuinfo[/HTML]

Got the following output:

[HTML]processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz
stepping        : 6
cpu MHz         : 1000.000
cache size      : 2048 KB
physical id     : 0
siblings        : 1
core id         : 255
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl est tm2 cx16 xtpr lahf_lm
bogomips        : 3333.39

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz
stepping        : 6
cpu MHz         : 1000.000
cache size      : 2048 KB
physical id     : 1
siblings        : 1
core id         : 255
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl est tm2 cx16 xtpr lahf_lm
bogomips        : 3325.16[/HTML]

Do I need to do the following?

[HTML]sudo apt-get install linux-686-smp[/HTML]

Thanks so much :)

---

### Post by Razorback on 2007-04-05
Check System Monitor Under System>Administration.  It is similar to task manager in windows.  It will show you the cpus if they are being utilized.

---

### Post by englishaugust on 2007-04-06
Thanks, checked system monitor and it shows both cpus :)

---

### Post by rajan on 2007-04-06
try 

```
 top 
``` 

too. it's not as cool looking, but it's got a lot of options. it worked on a lot of computers I was using that were dual processors and i can't imagine it wouldn't work with dual core processors.

---

### Post by Hortinstein on 2007-04-06
or install conky and have all your stats built into your desktop!

---

### Post by zanjabeel5 on 2007-04-27
deleted

---

