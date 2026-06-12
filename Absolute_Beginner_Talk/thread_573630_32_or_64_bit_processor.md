---
title: "32 or 64 bit processor?"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by conehead77 on 2007-10-11
How do i know if i have a 32 or 64 bit processor?
This is my /proc/cpuinfo:
```
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      : Intel(R) Pentium(R) 4 CPU 3.20GHz
stepping        : 3
cpu MHz         : 2800.000
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl est cid cx16 xtpr
bogomips        : 6389.78
clflush size    : 64

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      : Intel(R) Pentium(R) 4 CPU 3.20GHz
stepping        : 3
cpu MHz         : 2800.000
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl est cid cx16 xtpr
bogomips        : 6384.52
clflush size    : 64
```
Also, why is my 3,2 GHz processor running at 2,8 GHz??

---

### Post by om1 on 2007-10-11
you have a 32 bit processor bc its a intel p4

and your processor is set at "on demand" which is ok it will use its full power when it needs to

---

### Post by dcstar on 2007-10-11
> **om1 said:**
> you have a 32 bit processor bc its a intel p4

and your processor is set at "on demand" which is ok it will use its full power when it needs to

And it is a Dual Core CPU (almost 2 processors, but not quite..........)

---

### Post by misfitpierce on 2007-10-11
... Why does everyone assume P4 are all 32 bit... Google it they made 64 bit cpu's... Is your p4 fairly new? Im guessing it may be a 64 bit cpu considering it has 2MB cache. 

Observe...

[http://reviews.zdnet.co.uk/hardware/components/0,1000001694,39189912,00.htm](http://reviews.zdnet.co.uk/hardware/components/0,1000001694,39189912,00.htm)

I would say try installing 64 bit ubuntu and see if it installs through with 64 bit.

---

### Post by om1 on 2007-10-11
ok ill eat my words now....
and i think it is a 64 bit.... is that what this means? 
clflush size    : 64

---

### Post by misfitpierce on 2007-10-11
[http://www.lockergnome.com/nexus/it/2005/02/24/pentium-4-600-series-review-64-bit-double-the-cache/](http://www.lockergnome.com/nexus/it/2005/02/24/pentium-4-600-series-review-64-bit-double-the-cache/)

Even more info showing 6XX series of P4 quote "have double the L2 cache" = 2MB and are 64 bit. Enjoy :)

---

### Post by misfitpierce on 2007-10-11
> **om1 said:**
> ok ill eat my words now....
and i think it is a 64 bit.... is that what this means? 
clflush size    : 64


Not sure too sure about that. I've seen many diff numbers on cflush I believe so not sure. But chip should definatley be 64 bit.

---

### Post by rsambuca on 2007-10-11
What is the output of 

sudo lshw

---

### Post by conehead77 on 2007-10-11
> **rsambuca said:**
> What is the output of 

sudo lshw
quite a lot, but i think this is the relevant part:

```
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 3.20GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.4.3
          serial: 0000-0F43-0000-0000-0000-0000
          slot: Socket 478
          size: 2800MHz
          capacity: 2800MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht 
```

width: 64 bit :)

thanks for everybodies help, learned a lot again :guitar:

---

### Post by jediscout on 2007-10-11
My guess is also 64 bit since you seem to have a dual core. But I'm far from being an expert as of yet.

---

