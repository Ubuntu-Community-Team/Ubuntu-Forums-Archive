---
title: "Enable Dual-Core in Kubuntu on Dell Latitude D620"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by TMcKSmith on 2008-04-03
I just installed Kubuntu (Gutsy Gibbon) on a Dell Latitude D620 laptop.  I was browsing around google, and found that a few people mentioned Kubuntu only detects a single-core processor (as opposed to the Dual-Core 2 processor that I have in this laptop).  I was wondering how I can check and see if this is the case, and if so, how do I get it to recognize Dual-Core?  Thanks.

---

### Post by stchman on 2008-04-03
> **TMcKSmith said:**
> I just installed Kubuntu (Gutsy Gibbon) on a Dell Latitude D620 laptop.  I was browsing around google, and found that a few people mentioned Kubuntu only detects a single-core processor (as opposed to the Dual-Core 2 processor that I have in this laptop).  I was wondering how I can check and see if this is the case, and if so, how do I get it to recognize Dual-Core?  Thanks.

That is false.

Kubuntu is just KDE for Linux.  The real OS is the 2.6.xx-xx-generic and the generic kernel is multi processor capable.  Now if you have the 2.6.xx-xx-386 that is only single processor capable.  Ubuntu/Kubuntu defaults to the -generic kernel for SMP capability.

---

### Post by TMcKSmith on 2008-04-03
so...I should be okay?


also, I'm not sure if I should be trusting a Cardinals fan! (haha - kidding)  LETS GO PHILLIES

---

### Post by stchman on 2008-04-03
> **TMcKSmith said:**
> so...I should be okay?


also, I'm not sure if I should be trusting a Cardinals fan! (haha - kidding)  LETS GO PHILLIES

What kernel are you using?

---

### Post by herbster on 2008-04-03
Yeah, that is absolutely false. If the kernel has SMP compiled in it, it will detect multi cores, and Ubuntu's does.

You can see your CPU info with the comand:

```
cat /proc/cpuinfo
```

---

### Post by TMcKSmith on 2008-04-03
here's what I have:

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz
stepping        : 6
cpu MHz         : 1000.000
cache size      : 4096 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 3998.79
clflush size    : 64

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz
stepping        : 6
cpu MHz         : 1000.000
cache size      : 4096 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 3994.68
clflush size    : 64

---

### Post by shad0w_walker on 2008-04-03
That is listing two cores so it's working just fine. The whole Kubuntu not using two cores thing is bogus. I'm not upto scratch on my history so there may have been a time when the default kernel didn't support dual cores but that has definitely gone the way of the dinosaurs.

P.S. Welcome to the forums.

---

### Post by prem1er on 2008-04-03
Yes you should be ok with that ;)

Go Phills!

---

