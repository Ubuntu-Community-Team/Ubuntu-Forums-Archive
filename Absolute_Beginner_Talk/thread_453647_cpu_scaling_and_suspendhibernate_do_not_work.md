---
title: "cpu scaling and suspend/hibernate do not work"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by Adahn on 2007-05-24
rig is a socket 754 DFI Infinity nforce4 with a mobile athlon64.

/etc/init.d/powernowd: 156: cannot create /sys/devices/system/cpu/cpu0//cpufreq/scaling_governor: Directory nonexistent
* CPU frequency scaling not supported


I get that error when running that apt-get command. There is no 'module' folder in /etc either

suggestions?
I'm using 64 bit Feisty and the k8 kernel modules.

Scaling and suspend work fine in winxp.

---

### Post by Pragmatist on 2007-05-25
> **Adahn said:**
> 
I get that error when running **that apt-get command**...

Exactly what apt-get command are you running?

Have you seen this yet:
[https://help.ubuntu.com/community/SuspendHowto](https://help.ubuntu.com/community/SuspendHowto)

---

### Post by Adahn on 2007-05-25
sorry I wasn't more specific.

I've been using info from this thread:
[http://ubuntuforums.org/showthread.php?t=248867](http://ubuntuforums.org/showthread.php?t=248867)

this:
sudo modprobe powernow-k8
gets me this:
FATAL: Error inserting powernow_k8 (/lib/modules/2.6.20-15-generic/kernel/arch/x86_64/kernel/cpufreq/powernow-k8.ko): No such device


this:
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling
gives:
cat: /sys/devices/system/cpu/cpu0/cpufreq/scaling: No such file or directory


this:
cat /proc/cpuinfo
gets:
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 36
model name      : Mobile AMD Athlon(tm) 64 Processor 3400+
stepping        : 2
cpu MHz         : 910.715
cache size      : 1024 KB
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up pni lahf_lm
bogomips        : 1822.83
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc

---

### Post by Pragmatist on 2007-05-25
What happens if you start with a different kernel without the k8 modules.  Do you have a list of kernels to choose from when your system starts?

---

### Post by Adahn on 2007-05-25
I just have this kernel and the recovery one.

---

