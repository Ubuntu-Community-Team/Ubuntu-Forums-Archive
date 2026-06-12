---
title: "[SOLVED] what is my cpu type?"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by axemurder785 on 2007-08-23
Hello! I would like to know what my CPU type is because I want to download Cinelerra CV. 
these are the instructions it gives to get it for feisty:

"1. Make sure you have universe, multiverse and restricted repositories enabled
2. Add the following repository to your sources.list file, according to your CPU type:

- i686:
deb [http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/i686/](http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/i686/) ./
- athlonxp:
deb [http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/athlonxp/](http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/athlonxp/) ./
- pentium4:
deb [http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/pentium4/](http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/pentium4/) ./"

so I would like to know if my CPU is i686, athlonxp, or pentium4! please help! thanks in advance!

o and i also need help putting the correct repository in my "sources.list file".

---

### Post by nitro_n2o on 2007-08-23
```
less /proc/cpuinfo 
```

---

### Post by saj0577 on 2007-08-23
/\ /\ /\

---

### Post by axemurder785 on 2007-08-23
ok it said:

```
 processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Celeron(R) CPU 2.00GHz
stepping        : 7
cpu MHz         : 2000.064
cache size      : 128 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov 
pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up cid
bogomips        : 4003.91
clflush size    : 64 
```

which one is it? if it isn't any of them, which one would work best?

---

### Post by schorsch on 2007-08-23
... it should be an i686 ...

---

