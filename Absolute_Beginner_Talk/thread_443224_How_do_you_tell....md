---
title: "How do you tell..."
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by locke.dragon on 2007-05-14
if you have 64 bit Feisty or 32 bit Feisty?

---

### Post by taurus on 2007-05-14
```
uname -a
```

---

### Post by locke.dragon on 2007-05-14
i get this.  

```

link@aperturescience:~$ uname -a
Linux aperturescience 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux
link@aperturescience:~$ 

```

would that be 64 bit?

---

### Post by Nekiruhs on 2007-05-14
No thats 32 bit I'm pretty sure.

---

### Post by taurus on 2007-05-14
> **locke.dragon said:**
> i get this.  

```

link@aperturescience:~$ uname -a
Linux aperturescience 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 **[COLOR="Red"]i686[/COLOR]** GNU/Linux
link@aperturescience:~$ 

```

would that be 64 bit?

x86 (32bit).

---

### Post by Cypher on 2007-05-14
> **locke.dragon said:**
> i get this.  

```

link@aperturescience:~$ uname -a
Linux aperturescience 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux
link@aperturescience:~$ 

```

would that be 64 bit?
> **taurus said:**
> x86 (32bit).
Actually, all that is saying is that it's a 32-bit Kernel, not anything about the CPU. I get 
```

Linux Orion 2.6.20-1.2944.fc6 #1 SMP Tue Apr 10 18:46:45 EDT 2007 i686 athlon i386 GNU/Linux

```
on my AMD64 based machine, however I get:
```

$> cat /proc/cpuinfo

processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 79
model name      : AMD Athlon(tm) 64 Processor 3500+
stepping        : 2
cpu MHz         : 1000.000
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up pni cx16 lahf_lm svm cr8legacy ts fid vid ttp tm stc
bogomips        : 2005.20
clflush size    : 64

```

---

