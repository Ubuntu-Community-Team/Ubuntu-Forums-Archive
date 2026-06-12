---
title: "CPU MHz doesn't fitting the real MHz"
date: 2005-11-18
forum: Absolute Beginner Talk
---

### Post by NeoRc on 2005-11-18
This are some lines that I picked up from /proc/cpuinfo:

model name	: Mobile Intel(R) Pentium(R) 4     CPU 2.66GHz
stepping	: 9
cpu MHz		: 1595.647

Seems the "cpu MHz" is incorrent:( Should I change the value?

---

### Post by Kyral on 2005-11-18
You can't change the value

---

### Post by Kapre on 2005-11-19
[QUOTE=NeoRc]This are some lines that I picked up from /proc/cpuinfo:

model name	: Mobile Intel(R) Pentium(R) 4     CPU 2.66GHz
stepping	: 9
cpu MHz		: 1595.647

Seems the "cpu MHz" is incorrent:( Should I change the value?[/QUOTE]

NeoRc - Is your notebook a Celeron? Maybe that's the reason why it has a different cpu MHz description. I dont know if this is a bug that you should inform the devs.

K

---

### Post by MichaelM on 2005-11-19
Maybe it's frequency scaling?  :confused:

---

### Post by NeoRc on 2005-11-19
[QUOTE=Kapre]NeoRc - Is your notebook a Celeron? Maybe that's the reason why it has a different cpu MHz description. I dont know if this is a bug that you should inform the devs.
[/QUOTE]
Actually not, it's not a Celeron. Maybe it's frequency scaling, when I run the command *powernowd*, the output is like:
powernowd: Found 1 cpu:  -- 1 thread (or core) per physical cpu
powernowd:   cpu0: 1596Mhz - 2660Mhz (2 steps)

Does it mean everything goes well:confused:

---

### Post by heimo on 2005-11-19
Right click on panel, "Add to Panel..." choose "CPU Frequency Scaling Monitor" and see if the frequency changes under load (open some heavy applications).

---

### Post by NeoRc on 2005-11-19
heimo - I followed your suggestion, but there's just two values: 1.6GHz and 2.66GHz. No others!! When the task is busy, the value went up to 2.66GHz directly, and when the task is over, the value fell down to 1.6GHz, no other values.

---

### Post by prkfriryce on 2007-08-28
> **NeoRc said:**
> heimo - I followed your suggestion, but there's just two values: 1.6GHz and 2.66GHz. No others!! When the task is busy, the value went up to 2.66GHz directly, and when the task is over, the value fell down to 1.6GHz, no other values.

I'm seeing the same for the AMD Opteron:
```
cat /proc/cpuinfo 
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 39
model name      : AMD Opteron(tm) Processor 152
stepping        : 1
cpu MHz         : 2600.000
cache size      : 1024 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up pni lahf_lm ts fid vid ttp
bogomips        : 5230.89
clflush size    : 64

cat /proc/cpuinfo 
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 39
model name      : AMD Opteron(tm) Processor 152
stepping        : 1
cpu MHz         : 1000.000
cache size      : 1024 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up pni lahf_lm ts fid vid ttp
bogomips        : 2011.88
clflush size    : 64

2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux

```

---

