---
title: "[SOLVED] Dual-core 1.9GHz processor recognized as 1 GHz dual-core"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by piratesmack on 2007-12-12
Ubuntu is recognizing my dual-core 1.9GHz processor as a dual-core 1 GHz processor
I ran:
cat /proc/cpuinfo
and got:
processor : 0
vendor_id : AuthenticAMD
cpu family : 15
model : 107
model name : AMD Athlon(tm) 64 X2 Dual Core Processor 3600+
stepping : 1
cpu MHz : 1000.000
cache size : 512 KB
physical id : 0
siblings : 2
core id : 0
cpu cores : 2
fdiv_bug : no
hlt_bug : no
f00f_bug : no
coma_bug : no
fpu : yes
fpu_exception : yes
cpuid level : 1
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8legacy 3dnowprefetch ts fid vid ttp tm stc 100mhzsteps
bogomips : 2005.88
clflush size : 64
processor : 1
vendor_id : AuthenticAMD
cpu family : 15
model : 107
model name : AMD Athlon(tm) 64 X2 Dual Core Processor 3600+
stepping : 1
cpu MHz : 1000.000
cache size : 512 KB
physical id : 0
siblings : 2
core id : 1
cpu cores : 2
fdiv_bug : no
hlt_bug : no
f00f_bug : no
coma_bug : no
fpu : yes
fpu_exception : yes
cpuid level : 1
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8legacy 3dnowprefetch ts fid vid ttp tm stc 100mhzsteps
bogomips : 2005.88
clflush size : 64

Should I use the 64 bit version or something?

---

### Post by piratesmack on 2007-12-12
I'm using Gutsy

---

### Post by meborc on 2007-12-12
could it be possible, that due to powersaving or smth like this, the cpu gets clocked down to 1000... so to reduce the heat production? ... try running something cpu bogging... and see then

---

### Post by piratesmack on 2007-12-12
Dude thank you so much!
I was worried
I ran about 100 processes and it went up to 1.9GHz

---

### Post by meborc on 2007-12-12
> **piratesmack said:**
> Dude thank you so much!
I was worried
I ran about 100 processes and it went up to 1.9GHz

you see... linux can scale your cpu speed too :)

---

### Post by rfurman24 on 2007-12-12
It is called cool n' quite and can usually be disabled in bios if you do not like it.

---

### Post by piratesmack on 2007-12-12
Thanks

---

