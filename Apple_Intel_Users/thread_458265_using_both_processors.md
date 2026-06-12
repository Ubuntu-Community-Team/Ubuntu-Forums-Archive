---
title: "using both processors?"
date: 2007-05-29
forum: Apple Intel Users
---

### Post by buschi on 2007-05-29
Hi!

I have a C2D Macbook and installed Ubuntu 7.04. When I use programs that do a lot of computing and look at "top", it tells me in the headline "Cpu(s):  50%us" and in the table below in the column "%CPU": "100".

So I guess this application is using only one processor. Perhaps I misunderstood this completely, but isn't the operating system supposed to somehow distribute the load between the two cores? Or is this up to the application itself?

Thanks for clarification,
Sebastian.

---

### Post by tgm4883 on 2007-05-29
Both

The program must be written to take advantage of multiple processors (or cores)

But, if you run 2 programs that each take advantage of only 1 core, the OS will distribute each program to a different core

---

### Post by ronocdh on 2007-05-29
> **tgm4883 said:**
> Both

The program must be written to take advantage of multiple processors (or cores)

But, if you run 2 programs that each take advantage of only 1 core, the OS will distribute each program to a different core
This is true, however I believe the OP is complaining because the 32-bit (i386, basic desktop) version of Ubuntu is being used. With the Core2 Duo, the AMD64 version of Ubuntu should be installed, so as to take advantage of both cores. (The Core Duo is a 32-bit processor, and should be assigned the i386 version.)

The 64-bit forum is very helpful in this regard, and the guys there are generally great. Good luck and happy switching! ;)

---

### Post by tgm4883 on 2007-05-29
I disagree, the OP may be running the 32-bit version of Ubuntu, but that doesn't mean that it doesn't support dual core systems (I believe that the first Pentium D processors were dual core 32 bit processors.)

:EDIT:

With that being said, I agree that you should have the 64 bit version installed if you have a 64 bit processor (which the core 2 duo is)

:EDIT Again:

I don't remember where I read it and after doing a little research I can't find it.  So I retract my statement about the first Pentium D processors being 32-bit)  Although the 32-bit version of Ubuntu should still run dual core processors fine.

---

### Post by tgm4883 on 2007-05-29
If you want to see if the OS see's both cores, post the output of this from terminal

```
cat /proc/cpuinfo
```

Just for the heck of it, post this too

```
uname -r
```

---

### Post by mshale on 2007-05-31
> **tgm4883 said:**
> If you want to see if the OS see's both cores, post the output of this from terminal

```
cat /proc/cpuinfo
```

Just for the heck of it, post this too

```
uname -r
```

I did this, and it spat out info that i cannot decipher.  could you perhaps help us understand what is being output here?  I will post mine.  For example the first line says Processor    : 0  does that mean i have 0 processors? (joking of course!)  I just don't know what it all means.  What will the output of the core 2 duo look like?

```
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 13
model name      : Intel(R) Pentium(R) M processor 1.60GHz
stepping        : 8
cpu MHz         : 798.000
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe up est tm2
bogomips        : 1597.71
clflush size    : 64
```

Maybe just some of the relevant ones like clflush size and others?

Thanks so much

---

### Post by tgm4883 on 2007-05-31
Those are the different options that the processor has.  I dont know them all, i would try wikipedia.  Processor 0 is the 1st processor (we start counting at 0 in linux).  A dual core system looks like this.  I will post my core 2 duo later.

```
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 75
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
stepping        : 2
cpu MHz         : 2009.134
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm cr8_legacy
bogomips        : 4022.42
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 75
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
stepping        : 2
cpu MHz         : 2009.134
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm cr8_legacy
bogomips        : 4018.50
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc

```

---

### Post by tgm4883 on 2007-05-31
Core 2 Duo
```
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz
stepping        : 2
cpu MHz         : 1600.000
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx lm constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 3736.70
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz
stepping        : 2
cpu MHz         : 1600.000
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx lm constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 3733.36
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

```

---

### Post by ivesjd on 2007-05-31
Im pretty sure that both the Core Duos and the Core 2 Duos are both 32 bit. Could someone point to something saying otherwise?

---

### Post by buschi on 2007-05-31
> **ivesjd said:**
> ... Core 2 Duos ... 32 bit. ... something saying otherwise?

[http://www.apple.com/macbook/intel.html](http://www.apple.com/macbook/intel.html)


the only thing that made me stop using the 64bit version was that it wouldn't start up. i read that this was due to refit -- and that video codecs etc are no fun in a 64bit system. however, i understand that some people here managed successfully...

uname -r gives here: 2.6.20-16-generic .

best,
sebastian.

---

### Post by tgm4883 on 2007-05-31
> **ivesjd said:**
> Im pretty sure that both the Core Duos and the Core 2 Duos are both 32 bit. Could someone point to something saying otherwise?

You mean other than the fact im running the 64-bit version of Ubuntu Feisty on my Core 2 Duo right now?

Core 2 Duo
[http://www.intel.com/products/processor/core2duo/specifications.htm](http://www.intel.com/products/processor/core2duo/specifications.htm)

Or this for the Core Duo, which unofficially supports EM64T on their Yonah 
[http://www.hexus.net/content/item.php?item=4604](http://www.hexus.net/content/item.php?item=4604)

---

### Post by ivesjd on 2007-05-31
Thanks for the link! And I think you could run the 64bit version on a 32bit proc, its just not gonna run that great. I was more wondering about the macbooks and macbook pros. Has anyone seen any info on those specific processors?

---

### Post by tgm4883 on 2007-05-31
Nope, can't run a 64-bit OS on a 32-bit processor.  32-bit processor == 32-bit OS, 64-bit processor == 32 or 64 bit OS

---

### Post by ronocdh on 2007-05-31
> **tgm4883 said:**
> Nope, can't run a 64-bit OS on a 32-bit processor.  32-bit processor == 32-bit OS, 64-bit processor == 32 or 64 bit OS
Correct. It's common that people think having a 64-bit processor means you **must** run 64-bit Linux; not the case, although I highly recommend it! Users of 32-bit processors **must** run 32-bit Linux, though.

---

### Post by Gen2ly on 2007-05-31
Felicitations, I ripped this totally from the Gentoo-Wiki:

*The Core2Duo is processor that uses the IA-32 microarchitecture with EM64T extension. That makes it similar to an AMD Athlon 64 processor. Although it is not a true 64 bit processor (not IA-64 microarchitecture) it can process the 64bit instruction set and features the 64bit address register extensions and general purpose registers. That means you can choose to run a traditional 32bit x86 or an x86-64 system.*

Core Duos do not have this extension so 64 bit is impossible.  People have reported some speed gains with the 64bit, but I wouldn't call it anything remarkable.  Also people using 64bit will find not all programs will run 64bit.  There are usually workarounds though.

---

### Post by ronocdh on 2007-05-31
> **buschi said:**
> [http://www.apple.com/macbook/intel.html](http://www.apple.com/macbook/intel.html)


the only thing that made me stop using the 64bit version was that it wouldn't start up. i read that this was due to refit -- and that video codecs etc are no fun in a 64bit system. however, i understand that some people here managed successfully....
I call FUD. 64-bit Ubuntu boots just fine via rEFIt, and installing drivers (I'm talking proprietary ATI, i.e. fglrx) is exactly the same process. I see no reason to deal with reduced performance by using 32-bit Ubuntu on a 64-bit processor.

---

### Post by tgm4883 on 2007-06-01
> **Dirk.R.Gently said:**
> Felicitations, I ripped this totally from the Gentoo-Wiki:

*The Core2Duo is processor that uses the IA-32 microarchitecture with EM64T extension. That makes it similar to an AMD Athlon 64 processor. Although it is not a true 64 bit processor (not IA-64 microarchitecture) it can process the 64bit instruction set and features the 64bit address register extensions and general purpose registers. That means you can choose to run a traditional 32bit x86 or an x86-64 system.*

Core Duos do not have this extension so 64 bit is impossible.  People have reported some speed gains with the 64bit, but I wouldn't call it anything remarkable.  Also people using 64bit will find not all programs will run 64bit.  There are usually workarounds though.

Did a little checking.  I don't know if im reading this all right, but here it goes.  All from the wikipedia.

[http://en.wikipedia.org/wiki/Core_2_duo](http://en.wikipedia.org/wiki/Core_2_duo)
> Intel Core 2 processors feature Intel 64, Virtualization Technology (except T5500 or lower end E4x00), Execute Disable Bit, and SSE3. Core 2 also introduced SSSE3, LaGrande Technology[citation needed], Enhanced SpeedStep Technology, and Active Management Technology (iAMT2).

[http://en.wikipedia.org/wiki/IA-32#Next-generation_64-bit_Instruction_Sets](http://en.wikipedia.org/wiki/IA-32#Next-generation_64-bit_Instruction_Sets)
> IA-64

Intel's IA-64 architecture is not directly compatible with the IA-32 instruction set. It completely discards all IA-32 instructions, and starts from scratch with a completely different instruction set as well as using a VLIW design instead of out-of-order execution. IA-64 is the architecture used by the Itanium line of processors. Itanium initially had hardware-support for IA-32, but it was very slow. Intel shifted to the use of a software emulator instead. The nomenclature "IA-64" means "Intel Architecture, 64-bit", but the connection with IA-32 is only in the name.

Further improvements are:

    * Sixteen times the amount of general purpose registers (now 128)
    * Sixteen times the amount of floating point registers (now 128)
    * Register rotation mechanism to keep values in registers over function calls

[edit] AMD64

AMD's AMD64 instruction set, initially called x86-64, is largely built on top of IA-32, and thus maintains the x86 family heritage. While extending the instruction set, AMD took the opportunity to clean up some of the odd behaviour of this instruction set that has existed (plagued programmers?) since its earliest 16-bit days, while the processor is operating in 64-bit mode.

Further improvements are:

    * Two times the number of general purpose registers (now 16)
    * Two times the number of SSE registers (now 16)
    * The general purpose registers are now truly general-purpose registers and are no longer restricted.
    * Most of the functionality of the segment registers has been deprecated, since their usage has steadily declined even during the IA-32 days.

[edit] Intel 64

By February 2004, Intel announced the Intel 64 instruction set, formerly known as Yamhill. It was derived from AMD's AMD64. Intel 64 is generally compatible with code written for the AMD64, though it lacks some AMD64 features; for more details, read the Intel 64 article. Intel started using the set starting with the Xeon Nocona core in late 2004, introducing it to the desktop market with the Pentium 4 E0 revision in early 2005.

[http://en.wikipedia.org/wiki/Intel_64](http://en.wikipedia.org/wiki/Intel_64)
> x86-64 is a 64-bit microprocessor architecture and corresponding instruction set; it is a superset of the Intel x86 architecture, which it natively supports. It was designed by Advanced Micro Devices (AMD), who have since renamed it AMD64. This architecture has also been adopted by Intel under the name Intel 64 (formerly known as Yamhill, Clackamas Technology (CT), IA-32e, and most recently Extended Memory 64 Technology (EM64T)).[1] This leads to the common use of the names x86-64 or x64 as more vendor-neutral terms to collectively refer to the two nearly identical implementations.

So it would seem that the Core 2 Duo is a 64 bit processor

---

### Post by tgm4883 on 2007-06-01
> **ronocdh said:**
> I call FUD. 64-bit Ubuntu boots just fine via rEFIt, and installing drivers (I'm talking proprietary ATI, i.e. fglrx) is exactly the same process. I see no reason to deal with reduced performance by using 32-bit Ubuntu on a 64-bit processor.

Second the FUD call.  Not hard at all to get up and running

---

### Post by ronocdh on 2007-06-01
> **tgm4883 said:**
> Second the FUD call.  Not hard at all to get up and running
Thanks for the alley-oop accusation there. And thanks also for your intensive research! There's no question, gentlemen: Core Duo = 32-bit, while Core2 Duo = 64-bit processors.

And yes, to repeat, 64-bit processors can run 32-bit Linux, but 32-bit processors **cannot** run 64-bit Linux.

---

### Post by buschi on 2007-06-01
> **tgm4883 said:**
> Second the FUD call.  Not hard at all to get up and running

that's nice. i tried with feisty herd 4 and it did not boot.
can i ```
sudo aptitude install 64bit
```?

---

### Post by ronocdh on 2007-06-01
> **buschi said:**
> that's nice. i tried with feisty herd 4 and it did not boot.
can i ```
sudo aptitude install 64bit
```?
No, you really should back up all your data and then install fresh from the AMD64 CD of 7.04.

---

### Post by tgm4883 on 2007-06-01
First, has this been in the Apple Intel Users the whole time?  I usually don't post in here as I do not own an apple computer.  (Opps, my bad)

Sorry, installing the 64 bit version requires a complete reinstall.  I am not even sure if you can keep your setting.  (I have heard conflicting things on that)

Herd 4 was Alpha software.  I would bet that like most people on these forums, that your problem was with feisty.  (See any of the many threads on feisty freezing)

---

### Post by stmiller on 2007-06-01
> **buschi said:**
> 
can i ```
sudo aptitude install 64bit
```?

hehehe ;)

---

### Post by ronocdh on 2007-06-01
> **tgm4883 said:**
> First, has this been in the Apple Intel Users the whole time?  I usually don't post in here as I do not own an apple computer.
Yup. But your comments were very helpful! Come back anytime. ;)
> Sorry, installing the 64 bit version requires a complete reinstall.  I am not even sure if you can keep your setting.  (I have heard conflicting things on that)

Herd 4 was Alpha software.  I would bet that like most people on these forums, that your problem was with feisty.  (See any of the many threads on feisty freezing)
Word.

---

### Post by tgm4883 on 2007-06-01
> **ronocdh said:**
> Yup. But your comments were very helpful! Come back anytime. ;)


Didn't even notice it until today.  I search for unanswered posts and try to help there.

---

### Post by speedemonV12 on 2007-06-01
so what is the conclusion on this issue, I am running a Macbook Pro, core 2 duo, 2gb ram 160gb hard drive... should i run 32 bit ubuntu, or 64bit ubuntu, is there a large difference, will one or the other give me better performance? and if i should use 64bit ubuntu, you would like me to install the AMD64bit version, even tho im on an intel machine?

---

### Post by tgm4883 on 2007-06-01
> **speedemonV12 said:**
> so what is the conclusion on this issue, I am running a Macbook Pro, core 2 duo, 2gb ram 160gb hard drive... should i run 32 bit ubuntu, or 64bit ubuntu, is there a large difference, will one or the other give me better performance? and if i should use 64bit ubuntu, you would like me to install the AMD64bit version, even tho im on an intel machine?

Use 64-bit Ubuntu.  For normal tasks there isn't much difference.  Get into any graphics program, video editing, etc and you will notice a difference (other programs as well)  There is also problems running a 32 bit OS on some 64-bit hardware.  You paid for the hardware, why not use it?

And yes, your supposed to use the AMD64 version.  The only reason that it is called that is because AMD came out with 64-bit first (for consumers anyway)

---

### Post by speedemonV12 on 2007-06-01
ok thanks for the quick reply

---

