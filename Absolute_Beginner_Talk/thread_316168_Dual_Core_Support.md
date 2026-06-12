---
title: "Dual Core Support"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by zeroooooooooooo on 2006-12-10
I am running an AMD Athlon64 X2 4200+, Ubuntu Dapper (x86, not 64 bit), and I don't think it is set up to use both cores.  I saw another thread on this topic, but was unsure what applied to my case as well.  Here is the output of cat /proc/cpuinfo
```

zero@zero-desktop:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 43
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
stepping        : 1
cpu MHz         : 2211.473
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3d now pni lahf_lm cmp_legacy
bogomips        : 4427.47
```


Thanks for any help.

---

### Post by axle_foley00 on 2006-12-10
I noticed you said you were running Ubuntu Dapper, perhaps Edgy Eft has included support for Dual Core processors.

By chance was this the other post you saw?

[http://ubuntuforums.org/showthread.php?t=315228&highlight=dual+core](http://ubuntuforums.org/showthread.php?t=315228&highlight=dual+core)

As someone mentioned that Edgy should have support built in and someone else mentioned that you might need to "*install an *-smp kernel to get support for both CPUs ...*".

Hope that helps.

---

### Post by zeroooooooooooo on 2006-12-10
Ok, I got it working, thanks.

---

### Post by axle_foley00 on 2006-12-10
> **zeroooooooooooo said:**
> Ok, I got it working, thanks.

What solution did you end up using?

---

### Post by Choxo on 2006-12-24
As far as I know,
you have to use Generic Kernel...
That worked for me...

---

### Post by spockrock on 2006-12-24
if you are using edgy then the solution is to use the generic kernel, dapper and previous you have to install the linux-386-smp, linux-686-smp, linux-k7-smp, etc etc packages.

---

