---
title: "some problems after installation"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by andrewpb on 2006-12-27
so i just install 6.06 and i like what i see.  but there are some problems, i should first say that i don't know how to use the terminal yet but i want to learn how...

my programs are running slow, much slower than windows (what i'm switching from) and it even takes several seconds for the tabs at the top of the screen to load.  

i saw a thread earlier about one way to fix this, yet i didn't quite understand how to get to the point where they were at.  [http://www.ubuntuforums.org/showthread.php?t=317242&highlight=slow+app+startup](http://www.ubuntuforums.org/showthread.php?t=317242&highlight=slow+app+startup)

i think that may help me, but i don't know how to do that, any help would be awesome

---

### Post by anaconda on 2006-12-27
Have you got a dual core processor? 6.06 with a standard kernel doesn't support both processors! (6.10 does). And if you have energy saving features enabled from your BIOS, then you might be runnig your processor with just 1/2 speed (energy saving)!  

Does the output of the following command look right?
more /proc/cpuinfo
(type it in terminal -window.)
it tells you what processor ubuntu thinks you have. just check that the info is correct.

---

### Post by andrewpb on 2006-12-27
i typed it in and this is what pops out
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      : Mobile Intel(R) Pentium(R) 4 CPU 2.80GHz
stepping        : 1
cpu MHz         : 2790.246
cache size      : 1024 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov
pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pni monitor ds_cpl est tm2 cid xtpr
bogomips        : 5622.05


it looks as though the computer knows there is a processor there, but doesn't access it.  am i right, and how would i remedy that?

---

### Post by wipet on 2006-12-27
It would help to know your configuration (graphic card, etc).
Your processor is fine, I don't think it's the problem.
Also, what is the problem exactly? Does your applications are slow to open? Or are they operate slowly?

---

### Post by andrewpb on 2006-12-27
they open and run slowly, i don't know my graphics card off hand

---

