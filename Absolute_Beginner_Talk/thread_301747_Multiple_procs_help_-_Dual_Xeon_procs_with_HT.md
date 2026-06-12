---
title: "Multiple procs help - Dual Xeon procs with HT"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by NoFearDJB on 2006-11-17
I'm runing an IBM Z PRO with two Xeon dual-core procs. Thus, i have four processors. I'm using the generic kernel for xubuntu verision:
```
$ uname -r
2.6.17-10-generic

``` 
When I do a:
```
$ cat /proc/cpuinfo 
```
I get the following output:
```
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Xeon(TM) CPU 2.66GHz
stepping        : 7
cpu MHz         : 2658.517
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
bogomips        : 5322.10

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Xeon(TM) CPU 2.66GHz
stepping        : 7
cpu MHz         : 2658.517
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
bogomips        : 5316.53

processor       : 2
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Xeon(TM) CPU 2.66GHz
stepping        : 7
cpu MHz         : 2658.517
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
bogomips        : 5316.79

processor       : 3
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Xeon(TM) CPU 2.66GHz
stepping        : 7
cpu MHz         : 2658.517
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
bogomips        : 5316.57

```

So obviously, it detects all four procs, but when I'm running applications, I see that my CPU load maxes at 25% sometimes. Is this application dependent if it uses all four CPUs for processing power or do i need to do more to make xubuntu utilize all four procs? Other times, it goes to about 50% load... any way for me to be sure all procs can but utilized? Just want to make sure I'm getting the most out of my processors! Thanks in advance! :D :mrgreen:

---

### Post by po0f on 2006-11-17
NoFearDJB,

Most programs are single-threaded by nature, so even with one CPU-intensive process, all four "procs" won't get touched (I say procs loosely becasue HT != dual core).  I'm not sure how Linux slices time for processes and how they get distributed to the different processors.  Try compiling the following program and run it four times (it's just an infinite loop, and should eat up the CPU):
```
int main(void)
{
  for (;;) {};
  return 0;
}
```

---

### Post by Marsolin on 2006-11-18
I'm typing this on a dual Xeon with HT system. Since each processor represents 25% CPU utilization you are running into single threaded apps only being able to use a single proc at a time.

---

