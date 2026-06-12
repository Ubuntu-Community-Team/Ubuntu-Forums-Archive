---
title: "High CPU Usage"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by m60dude5 on 2008-03-29
Hi. I recently installed Ubuntu 7.10 and it is running great. However, my CPU usage seems to spike unexpectedly. I downloaded Htop and its output is in the screenshot attached. For some reason, it runs on 20 - 30 % idle, and jumps up to 90 - 100% when launching applications. I have an Intel Celeron 3.06 Ghz cpu and 2 GB of RAM so this is odd to me. In the picture attached, the CPU reads 100% but if you add the percents together it equals much less. Thanks for any help.

Also, can someone tell me why I have over 150 processes? Can I stop some of them from loading that I don't need?

---

### Post by NightwishFan on 2008-03-29
That seems to be some sort of bug I had it on one install of Xubuntu but I reinstalled and it went away. I am not really qualified to give you a good course of action. I am thinking it might be powernowd related.

---

### Post by m60dude5 on 2008-03-29
Does anyone know how I might undo the bug?

---

### Post by NightwishFan on 2008-03-29
Try disabling the powernowd service and restart.

---

### Post by Nythain on 2008-03-29
do me a favor... make sure your system is fairly idle (no exhaustive apps running) open up a terminal and type:
cat /proc/cpuinfo

copy the results, then in the terminal type:
glxgears &
once glxgears is running type:
cat /proc/cpuinfo
again, and copy the output that time...

basically we're gonna try to see for sure if its the powernowd... wich it sounds like it might... in a nutshell, ubuntu will try to scale the speed of your processor down when it doesnt need all the power, to cut back on power consumption and heat and all that jazz... cat /proc/cpuinfo should return two different processor speeds under the given circumstances above...

if it ultimately is the powernowd, i wouldnt worry too much about it... basically 100% of a scaled cpu isnt much, so it doesnt take much usage to hit 100%, and as long as it goes away (the spike you notice when opening apps or switching windows or whatnot) then its a pretty standard issue, and nothing to be alarmed about...

now if it sits at 100% cpu on something trivial for a prolonged time, then i would start to worry, and unfortunately, i cant provide you much help there

---

### Post by m60dude5 on 2008-03-29
Ok the output of sudo cat /proc/cpuinfo is:

```

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 6
model name      : Intel(R) Celeron(R) D CPU 3.06GHz
stepping        : 5
cpu MHz         : 3059.619
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 6
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc up pni monitor ds_cpl cid cx16 xtpr lahf_lm
bogomips        : 6123.26
clflush size    : 64

```

Once I get gears started, the output reads:

```

@matt-desktop:~$ 13665 frames in 5.0 seconds = 2732.889 FPS
ca14177 frames in 5.0 seconds = 2835.233 FPS
13664 frames in 5.0 seconds = 2732.635 FPS
13912 frames in 5.0 seconds = 2782.321 FPS
14334 frames in 5.0 seconds = 2866.717 FPS
13668 frames in 5.0 seconds = 2733.458 FPS

```
and it goes on

while gears is running the output reads:
```

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 6
model name      : Intel(R) Celeron(R) D CPU 3.06GHz
stepping        : 5
cpu MHz         : 3059.619
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 6
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc up pni monitor ds_cpl cid cx16 xtpr lahf_lm
bogomips        : 6123.26
clflush size    : 64

```

Thanks for the quick reply. How do I scale up the cpu for future reference if I need more power?

Thanks again.

---

### Post by m60dude5 on 2008-03-29
:popcorn:

---

