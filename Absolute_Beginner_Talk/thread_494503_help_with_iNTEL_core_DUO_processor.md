---
title: "help with iNTEL core DUO processor"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by cryo4.rm on 2007-07-07
Firstly i'd just like to thank the people that have answered my questions on this forum recently --------- im enjoying my first taste of linux and the ubuntu users' "community" has been a reassuring and supportive network of people.

 OK.. so my question

 my laptop has a Intel DUO processor... how can i know that ubuntu has recognised and takes advantage of both processors?

 i have just installed a processor monitoring "KARAMBA" application .... it shows only one processor being used ............. how can i corroborate this more formally...

 how can i set up ubuntu to use both CPUs???

 thanx ..

 joe

---

### Post by tgm4883 on 2007-07-07
post the output of 

cat /proc/cpuinfo

---

### Post by cryo4.rm on 2007-07-07
joe@stan:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2250  @ 1.73GHz
stepping        : 8
cpu MHz         : 798.000
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pni monitor est tm2 xtpr
bogomips        : 3461.81
clflush size    : 64

---

### Post by tgm4883 on 2007-07-07
hmm

Post the output of 

uname -a

---

### Post by cryo4.rm on 2007-07-07
output of
uname -a

Linux stan 2.6.20-16-386 #2 Thu Jun 7 20:16:13 UTC 2007 i686 GNU/Linux

---

### Post by tgm4883 on 2007-07-07
> **cryo4.rm said:**
> output of
uname -a

Linux stan 2.6.20-16-386 #2 Thu Jun 7 20:16:13 UTC 2007 i686 GNU/Linux

I don't think the i686 kernel has SMP enabled.  You need to install the generic kernel.

:EDIT:

Said "SMP installed" when I meant "SMP enabled"

---

### Post by por100pre1 on 2007-07-07
Another way is to use gnome-system-monitor .

It has a CPU monitor, it should show the load of two CPUs.

if it doesn't use the two processors:

sudo gedit /etc/init.d/rc

Find **CONCURRENCY=none** and change it to **CONCURRENCY=shell**

---

### Post by tgm4883 on 2007-07-07
> **por100pre1 said:**
> Another way is to use gnome-system-monitor .

It has a CPU monitor, it should show the load of two CPUs.

Unless i'm wrong, Not when the kernel only sees one CPU

---

### Post by por100pre1 on 2007-07-07
> **tgm4883 said:**
> Unless i'm wrong, Not when the kernel only sees one CPU

Of course, you get no argument from me about that. ;)

---

### Post by cryo4.rm on 2007-07-07
thankyou both.............

 where do enable SMP, where do i find the generic kernel?

---

### Post by HermanAB on 2007-07-07
When all else fails: [http://www.kernel.org](http://www.kernel.org)

Cheers,

Herman

---

### Post by AusIV4 on 2007-07-07
No need to go to kernel.org.

Did you swap out the processors after installing the OS? I installed feisty from the LiveCD on a Celeron M and got the 386 kernel, installed on a Core 2 duo and got the generic kernel. You should be able to install the generic kernel from synaptic. You may need to edit /boot/grub/menu.lst - just replace instances of '-386' with '-generic' and you should be good to go.

---

### Post by tgm4883 on 2007-07-07
Did you upgrade to feisty or do a fresh install

sudo apt-get install linux-image-generic

That will install the generic kernel, although you may also need to fix other things (ie, if you have restricted modules installed you will need to switch from the i386 modules to the generic modules)

---

