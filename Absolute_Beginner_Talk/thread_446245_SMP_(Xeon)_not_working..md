---
title: "SMP (Xeon) not working."
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by Centx on 2007-05-16
Hi, Ive got this problem with my dual Xeon CPU's: Ubuntu 7.04(and 6.06/6.10) do not recognize the second CPU (or at least it seems like it doesnt).  /proc/cpuinfo tells me there is two processors recognized, but I dont think both are physical, rather one ( 0 ) is, and the other ( 1 ) i s virtual, as Ive come to belive Xeon has this for some special maths or something.

The problem is obviously:
1. Get the second (or third and fourth) processor to work.
2. How to I check what processors are "real" and which are not.

thank you.
(If you need more info, just ask, and ill post it.)

the output from /proc/cpuinfo:
```
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 3
model name      : Intel(R) Xeon(TM) CPU 2.80GHz
stepping        : 4
cpu MHz         : 2800.344
cache size      : 1024 KB
physical id     : 0
siblings        : 1
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe lm constant_tsc pni monitor ds_cpl cid xtpr
bogomips        : 5604.66
clflush size    : 64

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 15
model           : 3
model name      : Intel(R) Xeon(TM) CPU 2.80GHz
stepping        : 4
cpu MHz         : 2800.344
cache size      : 1024 KB
physical id     : 3
siblings        : 1
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe lm constant_tsc pni monitor ds_cpl cid xtpr
bogomips        : 5600.69
clflush size    : 64

```

---

### Post by Marsolin on 2007-05-16
What kernel are you using?  It needs to be the generic version for SMP support.  I had the same problem you do, but didn't find a good solution.  I just disabled Hyper-Threading in BIOS to make sure I was using both physical processors.

---

### Post by Centx on 2007-05-16
> **Marsolin said:**
> What kernel are you using?  It needs to be the generic version for SMP support.  I had the same problem you do, but didn't find a good solution.  I just disabled Hyper-Threading in BIOS to make sure I was using both physical processors.

Thanks, ill try that then, and post result =).

---

### Post by Centx on 2007-05-16
Well, /proc/cpuinfo still shows two CPU's after i disabled Hyper Threading, so i guess it works. Dont think i need the logic processors anyway.

Thanks!! =)

---

