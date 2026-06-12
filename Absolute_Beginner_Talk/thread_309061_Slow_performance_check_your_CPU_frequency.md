---
title: "Slow performance: check your CPU frequency"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by flameproof on 2006-11-29
For those complaining (rightly) about poor Edgy performance, the problem is a bug in the CPU frequency scaling.

Check your CPU speed typing in Terminal: cat /proc/cpuinfo

You get then something like:

```
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 63
model name      : AMD Athlon(tm) 64 Processor 3500+
stepping        : 2
[COLOR="Red"]cpu MHz         : 1000.000[/COLOR]
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up pni lahf_lm ts fid vid ttp
bogomips        : 2007.25
```

Here the speed got stuck at 1000 MHz. So far there seem to be no solution, if somebody knows a link, please post it here.

Bug report and some discussions about it:

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/36014](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/36014)

[http://www.vmware.com/community/thread.jspa?messageID=321981&#321981](http://www.vmware.com/community/thread.jspa?messageID=321981&#321981)

---

