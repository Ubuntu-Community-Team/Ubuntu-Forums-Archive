---
title: "Enable dual-core in fiesty"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by Eezyville on 2008-02-25
How the heck do I enable dual-cores in Feisty Fawn? The system monitor only shows 1 core. :confused:

Here's some info: 
HP Pavillion dv9000
AMD Turion64 x2 2.2GHz

When I type in sudo cat /proc/cpuinfo I get:

```
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 72
model name      : AMD Turion(tm) 64 X2 Mobile Technology TL-60
stepping        : 2
cpu MHz         : 2009.204
cache size      : 512 KB
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
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up pni cx16 lahf_lm cmp_legacy svm cr8legacy ts fid vid ttp tm stc
bogomips        : 4021.72
clflush size    : 64

```

and when i type uname -a I get:
```
Linux Zengetsu 2.6.20-16-generic #2 SMP Tue Feb 12 05:41:34 UTC 2008 i686 GNU/Linux

```

Any answers?

---

### Post by Eezyville on 2008-02-26
I fixed the problem. For some reason nosmp was a boot option in my menu.lst in the grub folder. I took that option off.

EDIT: Now I can't suspend. :(

---

