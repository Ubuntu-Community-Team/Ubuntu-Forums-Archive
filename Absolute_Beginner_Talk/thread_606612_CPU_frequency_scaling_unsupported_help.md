---
title: "CPU frequency scaling unsupported help"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by laharl on 2007-11-08
I want to get this feature working but dont know how. It seems that my processor supports it. Is there anything I can do?

fresh@fresh-laptop:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 13
model name      : Intel(R) Celeron(R) M processor         1.50GHz
stepping        : 8
cpu MHz         : 1496.400
cache size      : 1024 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe up
bogomips        : 2995.97
clflush size    : 64

---

### Post by TeaSwigger on 2007-11-08
Perhaps these threads will be informative:
[http://ubuntuforums.org/showthread.php?t=582069](http://ubuntuforums.org/showthread.php?t=582069)
[http://ubuntuforums.org/showthread.php?t=190921](http://ubuntuforums.org/showthread.php?t=190921)
[http://ubuntuforums.org/showthread.php?t=394911](http://ubuntuforums.org/showthread.php?t=394911)

Luck :)

---

### Post by kvonb on 2007-11-08
-

---

### Post by bunny rabbit on 2007-11-14
Okay, did that. But how do I use it? I mean, isn't it possible to change the scale with powernowd?

---

### Post by skymera on 2007-11-14
can you enable speedstep in the BIOS?

---

### Post by spupy on 2007-11-28
> **bunny rabbit said:**
> Okay, did that. But how do I use it? I mean, isn't it possible to change the scale with powernowd?

I have almost the same CPU, but model 14 instead of model 13. This p4-clockmod works for me perfect. Check  this thread out: [http://ubuntuforums.org/showthread.php?t=582069]("http://ubuntuforums.org/showthread.php?t=582069")

---

