---
title: "CPU driver"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by Oki on 2006-11-17
Is there a way to check if I have the correct driver for my cpu? I remember I typed one command once to upgrade to the newer AMD but I just found a guide where you had to run two commands... And I never noticed any change in speed when upgrading. I have a AMD 3000+ 

When I add the CPU Frequency Scaling Monitor to the panel I get this error: 
“You will not be able to modify the frequency of your machine.  Your machine may be misconfigured or not have hardware support for CPU frequency scaling.”

Thanks!

---

### Post by taurus on 2006-11-17
```
cat /proc/cpuinfo
```

---

### Post by Oki on 2006-11-17
Witch gave me:

thomas@thomas-desktop:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 12
model name      : AMD Athlon(tm) 64 Processor 3000+
stepping        : 0
cpu MHz         : 2009.386
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext lm 3dnowext 3dnow
bogomips        : 4022.80

Do I have the last driver?

---

### Post by taurus on 2006-11-17
Well, looks like it is what you have then!  I am not sure what you mean with the latest CPU driver!!!  Do you actually mean the latest kernel?

---

### Post by kinematic on 2006-11-17
open a terminal and do the following:
sudo modprobe powernow-k8 cpufreq-userspace cpufreq-ondemand acpi
sudo apt-get install powernowd
sudo chmod +s /usr/bin/cpufreq-selector(changes permission for the cpu applet to let you scale it manually).
if this all works add powernow-k8,cpufreq-userspace,cpufreq-ondemand and acpi to /etc/modules

---

### Post by Oki on 2006-11-17
First command gave me this:
FATAL: Error inserting powernow_k8 (/lib/modules/2.6.15-27-k7/kernel/arch/i386/kernel/cpu/cpufreq/powernow-k8.ko): Unknown symbol in module, or unknown parameter (see dmesg)

Think I stop there:-)

I think I am talking about the kernel - so yes. I guess one command was correct.

---

### Post by kinematic on 2006-11-17
try powernow-k7

---

### Post by Oki on 2006-11-18
Witch gave me:

FATAL: Error inserting powernow_k7 (/lib/modules/2.6.15-27-k7/kernel/arch/i386/kernel/cpu/cpufreq/powernow-k7.ko): Unknown symbol in module, or unknown parameter (see dmesg)

---

### Post by kinematic on 2006-11-18
since you have an amd cpu your MoBo would support cool'n'quiet.....is it enabled in the bios?(just guessing here because i have an amd sempron and scaling works for me).

---

### Post by cantormath on 2006-11-18
isnt the K-7 a realllllllllly old chip?

---

### Post by Oki on 2006-11-18
I not turned the coll&q off. It works in Windows if I use the MSI cool&q software. 

K7 is the latest "kernel"/driver for Linux, I mena; when upgrading I had to type; sudo apt-get install linux-k7

---

### Post by kinematic on 2006-11-18
i just noticed this right now but ubuntu says you cpu does not support scaling.
thomas@thomas-desktop:~$ cat /proc/cpuinfo
processor : 0
vendor_id : AuthenticAMD
cpu family : 15
model : 12
model name : AMD Athlon(tm) 64 Processor 3000+
stepping : 0 <<<---- :-k 
cpu MHz : 2009.386
cache size : 512 KB
fdiv_bug : no
hlt_bug : no
f00f_bug : no
coma_bug : no
fpu : yes
fpu_exception : yes
cpuid level : 1
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext lm 3dnowext 3dnow
bogomips : 4022.80

---

### Post by Oki on 2006-11-19
Ok, thanks for the info - no stpping on me he he

---

