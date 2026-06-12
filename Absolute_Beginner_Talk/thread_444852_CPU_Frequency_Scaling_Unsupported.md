---
title: "CPU Frequency Scaling Unsupported"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by Lindworm on 2007-05-15
Hey,

I've put the cpu freq monitor on my panel but it says not supported. So I read in this:-

[http://ubuntuforums.org/showthread.php?t=316873](http://ubuntuforums.org/showthread.php?t=316873)

That I have to type sudo modprobe p4-clockmod for it to work but when I do

```
FATAL: Error inserting p4_clockmod (/lib/modules/2.6.20-15-generic/kernel/arch/i386/kernel/cpu/cpufreq/p4-clockmod.ko): No such device

```

Comes up. Help please, oh and also I have an amd athlon processor running at 1800 mhz.

Thanks,
Ben

---

### Post by tgm4883 on 2007-05-15
do this and post the output

```
cat /proc/cpuinfo
```

---

### Post by Bachstelze on 2007-05-15
How do you expect a driver with "P4" in it's name to work on an Athlon ? Try powernow_k7 or powernow_k8.

---

### Post by Lindworm on 2007-05-15
hymn that didn't work it says

FATAL: Error inserting powernow_k8 (/lib/modules/2.6.20-15-generic/kernel/arch/i386/kernel/cpu/cpufreq/powernow-k8.ko): No such device

and tgm:-

processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 6
model           : 10
model name      : AMD Athlon(tm) processor
stepping        : 0
cpu MHz         : 1800.055
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up ts
bogomips        : 3602.85
clflush size    : 32

Thanks,
Ben

---

### Post by Bachstelze on 2007-05-15
Oh, that's weird, I really thought I mentioned "powernow_k7" too...

---

### Post by Lindworm on 2007-05-15
I used that one to. Same error.

---

### Post by tgm4883 on 2007-05-15
Your processor doesn't support frequency stepping.

---

### Post by Lindworm on 2007-05-15
Oh okay. Was just an experiment.

---

### Post by moob on 2008-05-07
I have the same problem. CPU Frequency Scaling Monitor is telling me: **CPU frequency scaling unsupported**
But one week ago it was scaling correctly. Can you help me please?

cat /proc/cpuinfo:
```

processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 72
model name	: AMD Turion(tm) 64 X2 Mobile Technology TL-52
stepping	: 2
cpu MHz		: 1595.708
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy ts fid vid ttp tm stc
bogomips	: 3194.38
clflush size	: 64

processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 72
model name	: AMD Turion(tm) 64 X2 Mobile Technology TL-52
stepping	: 2
cpu MHz		: 1595.708
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy ts fid vid ttp tm stc
bogomips	: 3191.42
clflush size	: 64

```

modprobe p4-clockmod:
```
FATAL: Error inserting p4_clockmod (/lib/modules/2.6.24-17-generic/kernel/arch/x86/kernel/cpu/cpufreq/p4-clockmod.ko): No such device

```

---

### Post by tgm4883 on 2008-05-07
> **moob said:**
> I have the same problem. CPU Frequency Scaling Monitor is telling me: **CPU frequency scaling unsupported**
But one week ago it was scaling correctly. Can you help me please?

cat /proc/cpuinfo:
```

processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 72
model name	: AMD Turion(tm) 64 X2 Mobile Technology TL-52
stepping	: 2
cpu MHz		: 1595.708
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy ts fid vid ttp tm stc
bogomips	: 3194.38
clflush size	: 64

processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 72
model name	: AMD Turion(tm) 64 X2 Mobile Technology TL-52
stepping	: 2
cpu MHz		: 1595.708
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy ts fid vid ttp tm stc
bogomips	: 3191.42
clflush size	: 64

```

modprobe p4-clockmod:
```
FATAL: Error inserting p4_clockmod (/lib/modules/2.6.24-17-generic/kernel/arch/x86/kernel/cpu/cpufreq/p4-clockmod.ko): No such device

```

Did you read the whole thread?  To quote

> **HymnToLife said:**
> How do you expect a driver with "P4" in it's name to work on an Athlon ? Try powernow_k7 or powernow_k8.

---

### Post by moob on 2008-05-07
> **tgm4883 said:**
> Did you read the whole thread?  To quote
Well, i read it. I don't know what it means ("Try powernow_k7 or powernow_k8"). Mr. Google told me that it is module. But I don't know what exactly have to do. Sorry. Thanks.

---

