---
title: "can't install Athlon (k7) kernel dual core"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by madfrenzy on 2007-11-04
Hey I cant install Athlon (k7) kernel dual core via  "apt-get sudo apt-get install linux-k7-smp"  it says "Couldn't find package linux-k7-smp" so how to solve this prob??

---

### Post by overdrank on 2007-11-04
> **madfrenzy said:**
> Hey I cant install Athlon (k7) kernel dual core via  "apt-get sudo apt-get install linux-k7-smp"  it says "Couldn't find package linux-k7-smp" so how to solve this prob??

Hi and welcome, you may want to enable your repos. You can add repos under system, administration, software sources. The ubuntu software and updates tab. Hope this helps and good luck! 
[http://packages.ubuntu.com/dapper/base/linux-k7-smp](http://packages.ubuntu.com/dapper/base/linux-k7-smp)

---

### Post by madfrenzy on 2007-11-04
sorry but I'm a total newbie in Ubuntu ....so should I add the link in third party software tab or what?? and how to enable the repos??

---

### Post by ajgreeny on 2007-11-04
I think if you are running the generic kernel you already have the one you need that will deal with dual core processors.  The k7 kernel that used to be available in older versions of ubuntu is no longer available or needed.

---

### Post by madfrenzy on 2007-11-04
so if I dont need to install it so why is my ubuntu is very slow 

PC:
amd athlon dualcore 4200+
2 x 512 ddr1 
Nvidia geforce 6100

applicatins are very slow and often not responding especially with videos if freezes alot (I'm using xine btw)  
even if I reinstall ubuntu

---

### Post by joe.turion64x2 on 2007-11-04
> **madfrenzy said:**
> so if I dont need to install it so why is my ubuntu is very slow 

PC:
amd athlon dualcore 4200+
2 x 512 ddr1 
Nvidia geforce 6100

applicatins are very slow and often not responding especially with videos if freezes alot (I'm using xine btw)  
even if I reinstall ubuntu
That Athlon is not a K7 anymore, it is a K8. Have you installed the graphics driver?
Can you post the output of *cat /proc/cpuinfo*?

---

### Post by madfrenzy on 2007-11-04
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 43
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
stepping        : 1
cpu MHz         : 1000.000
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm cmp_legacy
bogomips        : 2010.90
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 43
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
stepping        : 1
cpu MHz         : 1000.000
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm cmp_legacy
bogomips        : 2010.90
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

---

### Post by joe.turion64x2 on 2007-11-04
> **madfrenzy said:**
> processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 43
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
stepping        : 1
cpu MHz         : 1000.000
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm cmp_legacy
bogomips        : 2010.90
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 43
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
stepping        : 1
cpu MHz         : 1000.000
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm cmp_legacy
bogomips        : 2010.90
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp
It seems frequency scaling is enabled. You did not answer if the graphics drivers were installed..I still thing they are responsible for your slow video performance but, anyway, you are using Gnome, aren't you? Right click in a panel, select "Add to panel" and add a couple of "Frequency Scaling Monitor" so you can select your processor's frequency from there.

---

### Post by snkmad on 2007-11-04
If you are using DDR1, then you have a Athlon64 Socket 939. Its indeed a K8.
But the strange thing is, its running @ 1Ghz speed, thats way too low.

Look in your bios for a "Cool'n Quiet" settings, turn it off.
Also look for the processor speed there.

It should be running @ 2.2Ghz each core. Something is wrong there.

---

### Post by madfrenzy on 2007-11-04
I installed nvidia restricted driver

---

### Post by madfrenzy on 2007-11-04
> **snkmad said:**
> 
It should be running @ 2.2Ghz each core. Something is wrong there.

yeah I noticed that now too

---

### Post by madfrenzy on 2007-11-04
........so how to change it??

---

### Post by madfrenzy on 2007-11-04
ok I changed the cpu frequency to 2.2 in the 2 core hope that this helps

---

### Post by joe.turion64x2 on 2007-11-04
Did you add the Frequency applet to your Gnome panel? It allows you to monitor your processor's frequency. If a processor supports Cool'n'quiet then it is a natural thing for it to slow down, the bad thing would be to be stuck in such a low frequency.

With the applets enabled you could run OpenOffice.org for example and see if the frequency changes.

EDIT: If it is set in 'On demand' mode, of course.

---

### Post by madfrenzy on 2007-11-04
I think nothing changed, it still takes long time to launch applications

---

### Post by snkmad on 2007-11-05
Have you disabled cool'n quiet on BIOS?

---

