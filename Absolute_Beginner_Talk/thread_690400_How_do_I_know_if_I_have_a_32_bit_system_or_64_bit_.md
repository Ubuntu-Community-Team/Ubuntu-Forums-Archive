---
title: "How do I know if I have a 32 bit system or 64 bit sytem?"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by SusieSA on 2008-02-07
Hi

I want to install some software to run DVDs on my pc, but I need to select what system I have - 32 bit or 64 bit.  

How do I know this?

Thanks
SusieSA

---

### Post by kizmet_x on 2008-02-07
Whats your processor?

---

### Post by Cypher on 2008-02-07
```

cat /proc/cpuinfo

```

---

### Post by SusieSA on 2008-02-07
cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 22
model name      : Intel(R) Celeron(R) CPU          420  @ 1.60GHz
stepping        : 1
cpu MHz         : 1600.029
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx lm constant_tsc up pni monitor ds_cpl tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 3201.66
clflush size    : 64

---

### Post by ~LoKe on 2008-02-07
```
uname -m
```
x86_64 is 64bit, anything else (i386, i686) is 32.

---

### Post by Cypher on 2008-02-07
Definitely 32-bit..

---

### Post by emarkd on 2008-02-07
Even if you have a 64-bit processor, you can't run 64-bit apps if you're using a 32-bit OS.  If you're using Ubuntu or some other Linux, you can find out what you're running by doing

```
uname -m
```

---

### Post by SusieSA on 2008-02-07
Thank you!

---

