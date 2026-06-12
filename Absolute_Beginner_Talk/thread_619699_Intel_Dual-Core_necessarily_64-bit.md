---
title: "Intel Dual-Core necessarily 64-bit?"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by pteri498 on 2007-11-21
I just bought a new computer. It's a Compaq SR5250NX system with an Intel Dual-Core 1.60GHz / 1.60GHz processor.

Does this make it necessarily 64 bit, or would it be stated explicitly somewhere?

Just wondering which architecture I should use.

Thanks!

---

### Post by mikewhatever on 2007-11-21
Not necessarily. Only core 2 duo models are 64 bits capable.
[http://en.wikipedia.org/wiki/Intel_Core_2](http://en.wikipedia.org/wiki/Intel_Core_2)

Intel made several dual core models which are 32 bits only, such as pentium D.
[http://en.wikipedia.org/wiki/Core_Duo](http://en.wikipedia.org/wiki/Core_Duo)

---

### Post by deadgobby on 2007-11-21
The 32 bit kernel has more software to run, but there has been more and more software for the 64 bit. The 64 bit kernel as not been as buggy in the pass. Still some stuff to iron out. Thus yes, you can run 32 bit kernel on a dual core machine.
Gobby

---

### Post by LaRoza on 2007-11-21
> **mikewhatever said:**
> Not necessarily. Only core 2 duo models are 64 bits capable.
[http://en.wikipedia.org/wiki/Intel_Core_2](http://en.wikipedia.org/wiki/Intel_Core_2)

Intel made several dual core models which are 32 bits only, such as pentium D.
[http://en.wikipedia.org/wiki/Core_Duo](http://en.wikipedia.org/wiki/Core_Duo)

The Pentium D is 64 bit, [http://en.wikipedia.org/wiki/List_of_Intel_microprocessors#64-bit_processors:_Intel64_-_NetBurst](http://en.wikipedia.org/wiki/List_of_Intel_microprocessors#64-bit_processors:_Intel64_-_NetBurst), unless there are more versions...

---

### Post by mikewhatever on 2007-11-21
> **LaRoza said:**
> The Pentium D is 64 bit, [http://en.wikipedia.org/wiki/List_of_Intel_microprocessors#64-bit_processors:_Intel64_-_NetBurst](http://en.wikipedia.org/wiki/List_of_Intel_microprocessors#64-bit_processors:_Intel64_-_NetBurst), unless there are more versions...

Thank you, did not know that.

---

### Post by scorp123 on 2007-11-21
> **pteri498 said:**
> I just bought a new computer. It's a Compaq SR5250NX system with an Intel Dual-Core 1.60GHz / 1.60GHz processor. Does this make it necessarily 64 bit, or would it be stated explicitly somewhere? You could boot the 32-bit Live CD, and once you're in the live desktop, open a terminal and then ask the CPU directly with this command: ```
cat /proc/cpuinfo
``` Now look for the so called "CPU flags". 64-bit CPU's have one with the name "lm" (= 'LM' ... for "long mode" which means 64-bit in programmer's speak). Example from my own laptop: ```
:~ > cat /proc/cpuinfo 
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2300  @ 1.66GHz
stepping        : 8
cpu MHz         : 1667.000
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
[COLOR="Red"]flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov 
pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc 
pni monitor est tm2 xtpr[/COLOR]
bogomips        : 3328.81
clflush size    : 64
``` I highlighted the relevant parts red above. As you can see the "lm" flag is missing in my output, so I am sure I have a 32-bit CPU, not a 64-bit one.

Shortened output from an AMD64 CPU which definitely is a 64-bit CPU: ```
:~# cat /proc/cpuinfo
processor       : 3
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 65
model name      : Dual-Core AMD Opteron(tm) Processor 2216
stepping        : 2
cpu MHz         : 1000.000
cache size      : 1024 KB
physical id     : 1
siblings        : 2
core id         : 1
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
[COLOR="Red"]flags         : fpu vme de pse tsc msr pae mce cx8 apic 
sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall 
nx mmxext fxsr_opt **_lm_** 3dnowext 3dnow pni cx16 lahf_lm 
cmp_legacy svm cr8legacy ts fid vid ttp tm stc[/COLOR]   
bogomips        : 1995.81
clflush size    : 64 
``` As you can see above, the system here has the "lm" flag, and thus this really is a 64-bit system.

As I wrote above you can easily verify yourself with a 32-bit Live CD what your CPU will say about itself.

---

### Post by gn2 on 2007-11-21
> **mikewhatever said:**
> Not necessarily. Only core 2 duo models are 64 bits capable.
[http://en.wikipedia.org/wiki/Intel_Core_2](http://en.wikipedia.org/wiki/Intel_Core_2)

Intel made several dual core models which are 32 bits only, such as pentium D.
[http://en.wikipedia.org/wiki/Core_Duo](http://en.wikipedia.org/wiki/Core_Duo)

> **LaRoza said:**
> The Pentium D is 64 bit, [http://en.wikipedia.org/wiki/List_of_Intel_microprocessors#64-bit_processors:_Intel64_-_NetBurst](http://en.wikipedia.org/wiki/List_of_Intel_microprocessors#64-bit_processors:_Intel64_-_NetBurst), unless there are more versions...

To clarify, Core Duo is a laptop CPU and is 32-bit only.
Core 2 Duo can be either desktop or laptop and all are 32 and 64-bit capable.
Pentium Duo T models are low end 32-bit Core Duo laptop CPU's
Pentium Duo E models are low end Core 2 Duo desktop CPU's and all are 32 and 64-bit capable.
Pentium D are desktop only and all are 32 and 64-bit capable.

---

