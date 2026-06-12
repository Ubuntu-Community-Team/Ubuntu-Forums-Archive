---
title: "Ubuntu 7.04:  How to tell if both cores of dual-core cpu are being used?"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by timzak on 2007-04-30
I have Ubuntu 7.04 and an Intel Core2Duo processor.  I'm a complete newbie and have just gotten Ubuntu set up (for the most part) how I like.  I still know very little about the terminal (just enough to copy/paste into it).  With that in mind, is there a way I can verify that both cores are being used on my processor?  I can't remember during the install process if there was some option to tell the OS if I've got a dual core cpu?  I seem to remember something about AMD64 vs. x86, but don't know if that has anything to do with dual core being enabled in the OS.  How can I tell?

Thanks.

---

### Post by compiledkernel on 2007-04-30
hmmm, if you open up a terminal and type 

sudo cat /proc/cpuinfo 

what does it output?

---

### Post by timzak on 2007-04-30
> 
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU          4300  @ 1.80GHz
stepping        : 2
cpu MHz         : 2395.084
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe lm constant_tsc pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 4792.81
clflush size    : 64

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU          4300  @ 1.80GHz
stepping        : 2
cpu MHz         : 2395.084
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe lm constant_tsc pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 4790.18
clflush size    : 64

I guess both cores are recognized and used then.  Thanks for the help.

---

