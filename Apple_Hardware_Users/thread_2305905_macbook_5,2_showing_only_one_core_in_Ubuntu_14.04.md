---
title: "macbook 5,2 showing only one core in Ubuntu 14.04"
date: 2015-12-10
forum: Apple Hardware Users
---

### Post by mho3 on 2015-12-10
I installed Trusty Tar from a CD image ([ubuntu-14.04.3-desktop-amd64+mac.iso]("http://cdimage.ubuntu.com/ubuntu/releases/14.04/release/ubuntu-14.04.3-desktop-amd64+mac.iso")) and using rfind.
Everything seems to work. Accept there is only one core out of two available.

Output to [B]cat /proc/cpuinfo
[/B]```
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Intel(R) Core(TM)2 Duo CPU     P7350  @ 2.00GHz
stepping    : 10
microcode    : 0xa07
cpu MHz        : 1995.000
cache size    : 3072 KB
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
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm dtherm tpr_shadow vnmi flexpriority
bugs        :
bogomips    : 3979.98
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:
```
Also I checked the solution in [this thread]("http://ubuntuforums.org/showthread.php?t=1631926"). But is does not work for me.
Then I tested several different kernels: 3.19 (default), 3.16, 3.13 . All of them with the same behaviour. Only the 4.2 kernel uses two cores. However under 4.2 I could not get the wifi running.

Any ideas how to enable multiple cores for a kernel <= 3.19 ?
Please find attached my compressed /var/log/kern.log: [ATTACH]266073[/ATTACH]

---

