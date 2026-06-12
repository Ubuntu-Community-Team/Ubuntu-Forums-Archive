---
title: "Intel Dual Core Query"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by glenm on 2007-02-08
I've installed Kubuntu 6.10 on an Intel Core 2 Duo.  It has an MSI 965 motherboard, 1 GB ram, 3 SATA drives and an IDE drive and IDE DVD.

Along with other bits and pieces I installed SuperKaramba with several monitoring widgets (kubuntu monitor and chilehardware).  Both of these say they will monitor 2 processors.

CPU 2 is shown at 0 percent usage at all times.

How can I verify that the second CPU is/is not being used and if its not being used how do I enable it?

uname output is 
Linux glen-desktop 2.6.17-10-generic #2 SMP Tue Dec 5 21:16:35 UTC 2006 x86_64 GNU/Linux

 Thanks
GlenM:confused:

---

### Post by bikeboy on 2007-02-08
Not sure but maybe running "top" in konsole will give you an idea.

---

### Post by mikewhatever on 2007-02-08
The command to verify CPU usage/info is 
> cat /proc/cpuinfo
here is the outcome of mine
> processor       : 0
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
bogomips        : 3329.72

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
bogomips        : 3324.96


---

### Post by lamego on 2007-02-08
> CPU 2 is shown at 0 percent usage at all times.
I have also found strange the same scenario when compiling applications, I always only got 50% of the cpu usage. Using "make -j2" which launches 2 processes during compilation did use 100% of the processor.
My understanding that a "typical" application runs on a single process and that will is only able to use one of COREs.

---

### Post by glenm on 2007-02-09
Both top and cat proc/cpuinfo tell me I only have a single cpu.  I cannot see anything in the BIOS that restricts to number of cores. 

The output of cat /proc/cpuinfo is

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz
stepping        : 6
cpu MHz         : 2400.000
cache size      : 4096 KB
physical id     : 0
siblings        : 1
core id         : 0
cpu cores       : 1
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx lm constant_tsc pni monitor ds_cpl vmx est tm2 cx16 xtpr lahf_lm
bogomips        : 4795.48
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

---

### Post by glenm on 2007-02-10
This may be a problem with Ubuntu 64 bit.  I found this thread [http://www.ubuntuforums.org/showthread.php?t=345569](http://www.ubuntuforums.org/showthread.php?t=345569) and even though I use the Generic kernel I still ony see 1 CPU - I may have to revert to 32 bit

---

