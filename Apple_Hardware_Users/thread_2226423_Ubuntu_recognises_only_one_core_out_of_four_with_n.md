---
title: "Ubuntu recognises only one core out of four with nolapic booting option"
date: 2014-05-27
forum: Apple Hardware Users
---

### Post by eugene.balkind on 2014-05-27
I have a problem similar to one in

[http://ubuntuforums.org/showthread.php?t=1084622](http://ubuntuforums.org/showthread.php?t=1084622)
[http://ubuntuforums.org/showthread.php?t=1740798](http://ubuntuforums.org/showthread.php?t=1740798)
[http://ubuntuforums.org/showthread.php?t=1631926](http://ubuntuforums.org/showthread.php?t=1631926)

i.e. my ubuntu does not see all cores of my CPU. It looks like I found the reason: I boot with ```
nolapic
``` option that eventually turns them off. However, this is the only way I know to boot on my machine (it's iMac, and all other boot options end up with a purple screen and no boot).

The output of my ```
cat /proc/cpuinfo
``` is as follows:
```
processor    : 0vendor_id    : GenuineIntel
cpu family    : 6
model        : 60
model name    : Intel(R) Core(TM) i7-4770S CPU @ 3.10GHz
stepping    : 3
microcode    : 0x17
cpu MHz        : 3101.000
cache size    : 8192 KB
physical id    : 0
siblings    : 1
core id        : 0
cpu cores    : 1
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 hle avx2 smep bmi2 erms invpcid rtm
bogomips    : 6185.95
clflush size    : 64
cache_alignment    : 64
address sizes    : 39 bits physical, 48 bits virtual
power management:

```

I would really appreciate if anyone can help me with this issue, as I would really like to use the power of all four of my cores.

---

