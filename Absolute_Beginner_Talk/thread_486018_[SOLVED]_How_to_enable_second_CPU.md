---
title: "[SOLVED] How to enable second CPU?"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by vegetable on 2007-06-27
it finally occured to me to ask for help regarding ubuuntu not detecting my second CPU, it's been a year already :roll: My second CPU is good because windows detects it just fine. what could be the problem? thanks for any help guys!

cat /proc/cpuinfo
```
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 6
model           : 10
model name      : AMD Athlon(tm) MP 2800+
stepping        : 0
cpu MHz         : 2133.652
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mp mmxext 3dnowext 3dnow
bogomips        : 4272.01

```

---

### Post by reckless2k2 on 2007-06-27
when you run the command, do you get a processor 1 after the processor 0? i have an Intel HT and your processors will show grouped as 0 then grouped as 1. If you are still not getting this, try installing the smp kernel for amd.

---

### Post by vegetable on 2007-06-27
which package do you think is the correct one?

**apt-cache search amd smp kernel**
```
kernel-headers-2.4.27-2-k7-smp - Linux 2.4.27 kernel headers for AMD K7 SMP
kernel-image-2.4.27-2-k7-smp - Linux kernel image for version 2.4.27 on AMD K7 SMP
kernel-pcmcia-modules-2.4.27-2-k7-smp - Mainstream PCMCIA modules 2.4.27 on AMD K7 SMP
linux-headers-2.6.15-23-k7 - Linux kernel headers 2.6.15 on AMD K7 SMP/UP
linux-image-2.6.15-23-k7 - Linux kernel image for version 2.6.15 on AMD K7 SMP/UP
linux-image-2.6.15-23-server-bigiron - Linux kernel image for version 2.6.15 on BigIron Server Equipment
linux-headers-2.6.15-25-k7 - Linux kernel headers 2.6.15 on AMD K7 SMP/UP
linux-headers-2.6.15-26-k7 - Linux kernel headers 2.6.15 on AMD K7 SMP/UP
linux-headers-2.6.15-27-k7 - Linux kernel headers 2.6.15 on AMD K7 SMP/UP
linux-headers-2.6.15-28-k7 - Linux kernel headers 2.6.15 on AMD K7 SMP/UP
linux-image-2.6.15-25-k7 - Linux kernel image for version 2.6.15 on AMD K7 SMP/UP
linux-image-2.6.15-25-server-bigiron - Linux kernel image for version 2.6.15 on BigIron Server Equipment
linux-image-2.6.15-26-k7 - Linux kernel image for version 2.6.15 on AMD K7 SMP/UP
linux-image-2.6.15-26-server-bigiron - Linux kernel image for version 2.6.15 on BigIron Server Equipment
linux-image-2.6.15-27-k7 - Linux kernel image for version 2.6.15 on AMD K7 SMP/UP
linux-image-2.6.15-27-server-bigiron - Linux kernel image for version 2.6.15 on BigIron Server Equipment
linux-image-2.6.15-28-k7 - Linux kernel image for version 2.6.15 on AMD K7 SMP/UP
linux-image-2.6.15-28-server-bigiron - Linux kernel image for version 2.6.15 on BigIron Server Equipment
linux-k7-smp - Complete Linux kernel on AMD K7 SMP
```

thanks for the help!

EDIT: i went with linux-k7-smp. Only choice anyway :)

---

### Post by vegetable on 2007-06-27
it worked. processor 1 shows up right after the whole processor 0 listing. I'm flying now! weee. Thanks reckless2k2, I would've never guessed the kernel

---

### Post by reckless2k2 on 2007-06-27
sorry i just saw the respond. yeah you picked the right one which is the generic linux-k7-smp. that was the correct one. enjoy.

---

### Post by drhiii on 2007-06-29
I read this post and understand that my installation is not recognizing my second processor.  And Intel based CPU, two processor setup.  I did a search for a corresponding kernel but did not see Intel listed.  

Can anyone make a recommendation on the correct smp kernel to apt-get so that it sees both processors?  Tx....


processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      : Intel(R) Xeon(TM) CPU 2.80GHz
stepping        : 3
cpu MHz         : 2800.259
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 3
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx 
fxsr sse sse2 ss ht tm pbe lm pni monitor ds_cpl cid cx16 xtpr
bogomips        : 5604.91

---

### Post by drhiii on 2007-06-29
Ops, after further study, I think I solved the two processor issue.

Another question, what does it mean if I have 4 processors showing up?  Meaning now I have processor 0, 1, 2 and 3??  But there are only two CPUs in the machine.  Thoughts anyone?

---

### Post by reckless2k2 on 2007-06-29
you must have a quad core cpu and not know it. the new intels are quad core. core 2 duo..core 2 extreme..etc

edit: i just looked at your proc info...haha...xeons are dual core. if you have 2 xeons...quad core....i think the new xeons are quad core as well.

---

### Post by mzar on 2007-06-29
What meaning of bogomips?

---

### Post by reckless2k2 on 2007-06-29
[http://en.wikipedia.org/wiki/BogoMips](http://en.wikipedia.org/wiki/BogoMips)

---

