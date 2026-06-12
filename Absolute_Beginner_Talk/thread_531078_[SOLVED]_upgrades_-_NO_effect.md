---
title: "[SOLVED] upgrades - NO effect?"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by sonicborg on 2007-08-21
Hey all, i have just changed from a 3700 single core to a 4200 x2 (still socket 939. and put in an extra 1gb of ram.

I am not noticing any difference what so ever. even when i try things like playing WoW, i am not gettign any performance boost. is there something i need to do, to tell linux that i have a faster/x2 processor, and make use of the extra ram ? or is it automatic ?

I really dont want to have to bother recompiling an entire kernel, i havent done that in years when i ran linux, was hoping by now linux might have got passed doing everything manually. :KS

---

### Post by ddrichardson on 2007-08-21
You should be able to install an SMP kernel through Synaptic/apt-get.

---

### Post by asmoore82 on 2007-08-21
> **sonicborg said:**
> Hey all, i have just changed from a 3700 single core to a 4200 x2 (still socket 939. and put in an extra 1gb of ram.

I am not noticing any difference what so ever. even when i try things **like playing WoW**, i am not gettign any performance boost. is there something i need to do, to tell linux that i have a faster/x2 processor, and make use of the extra ram ? or is it automatic ?

I really dont want to have to bother recompiling an entire kernel, i havent done that in years when i ran linux, was hoping by now linux might have got passed doing everything manually. :KS

What video card do you have?

---

### Post by sonicborg on 2007-08-21
i have a ati x600. not great, but i still expected a bit more performance, not just in wow, than what i got. i went from 1gb to 2gb ram, and the proc was single core amd 3700 changed to dual fore 4200.  but nothing on the system seems to make much/any difference :(

i did just order a new graphcis card (gone nvidia as i read thats better driver support than ati in linux) 

sorry to be dumb, whats SMP ?

---

### Post by ddrichardson on 2007-08-21
symetric multi processing. In other words multiple processors. I believe it needs to be an SMP kernel for Dual Core processors.

---

### Post by schorsch on 2007-08-21
SMP stands for Symmetric Multi Processing; the SMP Kernel enables the second core.
What is the output of
```
cat /proc/cpuinfo
uname -a
```

---

### Post by sonicborg on 2007-08-21
Thanks for help guys..

Uname = 
```
 Linux Lynx 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux

```
CPUinfo =
```
tyme@Lynx:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 35
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
stepping        : 2
cpu MHz         : 1000.000
cache size      : 512 KB
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
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm cmp_legacy ts fid vid ttp
bogomips        : 2001.44
clflush size    : 64

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 35
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
stepping        : 2
cpu MHz         : 1000.000
cache size      : 512 KB
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
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm cmp_legacy ts fid vid ttp
bogomips        : 2001.44
clflush size    : 64

```

---

### Post by igknighted on 2007-08-21
SMP is enabled.  I would ask that you run the command "free" to ensure that your new memory was recognized (just make sure the total matches what you expect).  After that, it must be a vid card issue.  I ran an x800 for a long time and then "upgraded" to an Nvidia 6600gt.  In windows, the ATI card is much better, but on linux the Nvidia card cleans house.  I am willing to bet this is the source of your issues.

---

### Post by sonicborg on 2007-08-21
hehe, cleans houses.. i like that, atleast the room i am sitting in nnow would be nice......

Yer the free command shows what i am expecting, maybe i am just greedy and expected a bit more of a system boost that what i got. :( 
i get the new graphics card tomorrow morning so hopefully will see my games fps go up.

---

