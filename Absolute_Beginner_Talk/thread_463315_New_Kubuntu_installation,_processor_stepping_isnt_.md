---
title: "New Kubuntu installation, processor stepping isnt detected correctly"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by ejw2076 on 2007-06-03
:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz
stepping        : 6
cpu MHz         : 2142.000
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
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 5015.28
clflush size    : 64

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz
stepping        : 6
cpu MHz         : 2142.000
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
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 5011.88
clflush size    : 64


I do have this processor overclocked to 2.5 gigs in the bios, as the stepping should be 7 instead of 6.  This seems like a problem that would be very difficult to correct for someone who is new with the os.  Does Kubuntu have some sort of support to where it lowers the stepping to conserve power?

---

### Post by raeb on 2007-06-03
You can't change your processors stepping, it's part of the manufacturing process and denotes how "mature" the current chip design is (they all go through minor revisions in their lifetime, and those are reflected in the stepping).

---

### Post by ejw2076 on 2007-06-03
What I meant is that the processor has a step of 7, the OS is reading it as a 6.  I'm guessing that there isn't a fix for this.

---

### Post by raeb on 2007-06-04
> **ejw2076 said:**
> What I meant is that the processor has a step of 7, the OS is reading it as a 6.  I'm guessing that there isn't a fix for this.

Only a kernel update I would think.  Don't sweat it tho as it doesn't adversly affect your system in any way.

---

