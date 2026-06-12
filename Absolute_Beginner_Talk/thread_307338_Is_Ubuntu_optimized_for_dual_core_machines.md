---
title: "Is Ubuntu optimized for dual core machines"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by pillu on 2006-11-26
Hi,

I don't have a real problem per se but a small question. I have got a new intel core duo laptop and have installed Ubuntu 6.06 Dapper on it. A techy friend of mine was telling me that its a bad idea because Ubuntu cannot fully utilize both processors as efficiently as Windows can. How true is his conjecture ?

Thanks

---

### Post by aysiu on 2006-11-26
I highly doubt it. Otherwise, [System 76](http://www.system76.com) wouldn't bother selling Intel Core Duo laptops at all.

---

### Post by meborc on 2006-11-26
i have a core 2 duo 6600 in my desk-computer... i'm running edgy and generic kernel on it... on system monitor i can see the 2 separate processor cores... so i see that both have been recognized and both working fine... :)

---

### Post by Shuja on 2006-11-26
Thats funny I've always seen linux use multiple processors more efficently than windows ;)

---

### Post by zgornel on 2006-11-26
Performance should be more or less the same, I gues slightly better on linux.

---

### Post by pillu on 2006-11-26
> **meborc said:**
> i have a core 2 duo 6600 in my desk-computer... i'm running edgy and generic kernel on it... on system monitor i can see the 2 separate processor cores... so i see that both have been recognized and both working fine... :)

On my system monitor, I can just see CPU history. And it graphs just one line. My device manager shows that my processor is unknown. How do I check if both my cores have been recognized or not ?

---

### Post by drphilngood on 2006-11-26
> **pillu said:**
> On my system monitor, I can just see CPU history. And it graphs just one line. My device manager shows that my processor is unknown. How do I check if both my cores have been recognized or not ?

Enter this in a terminal:
```
cat /proc/cpuinfo
```

---

### Post by diepruis on 2006-11-26
You need to install a new kernel to get the other CPU recognised, after you have done this Linux will use your CPU just as - if not more - efficiently as Windows.  The entire process should take a few minutes, and then you have to wait for the download.

Ask your friend where he gets his information from. Many people are seriously uneducated about Linux in general - even if they are techies. You can find information about installing a new kernel on these forums.

---

### Post by Ozitraveller on 2006-11-26
> **pillu said:**
> On my system monitor, I can just see CPU history. And it graphs just one line. My device manager shows that my processor is unknown. How do I check if both my cores have been recognized or not ?

Which Kernel are you using?

---

### Post by pillu on 2006-11-26
This is what I get for cat /proc/cpuinfo
> anand@zorg:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz
stepping        : 6
cpu MHz         : 1662.474
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm pni monitor ds_cpl est tm2 cx16 xtpr lahf_lm
bogomips        : 3328.46


To get the kernel version, google told me to do uname -r. The results are posted below
> anand@zorg:~$ uname -r
2.6.15-23-386


So are my two cores recognized ??

---

### Post by zgornel on 2006-11-26
No. Do a 'uname -a' if you see a #2 means that there are 2 active cpus/cores. If you see #1, you get the point. Install the 686 kernel to get the smp support (for 2 cores).

---

### Post by moilzpoil on 2006-11-26
So I tried the "uname -a" and find the #2 as well as i686.  How much performance am I loosing in average applications if I did the standard update to Edgy from Dapper?  Or does the upgrade detect the dual cores and configure accordingly?

---

### Post by houstonbofh on 2006-11-26
Your friend is wrong, but you do have a problem.  In 6.06 a 386 kernal is used.  You need to manually add the 686 and/or smp kernals.  You can do this in synaptic or type > sudo apt-get install linux-686-smp  You may also need linux-restricted-modules-686 if you are using them.  In edgy, it is all done automagically.

---

### Post by qamelian on 2006-11-26
> **zgornel said:**
> No. Do a 'uname -a' if you see a #2 means that there are 2 active cpus/cores. If you see #1, you get the point. Install the 686 kernel to get the smp support (for 2 cores).
This isn't quite accurate. I get the #2 and I am not using a dual core CPU. I think the #2 is only indicating that the kernel can support dual cores.

---

### Post by diepruis on 2006-11-27
> **qamelian said:**
> This isn't quite accurate. I get the #2 and I am not using a dual core CPU. I think the #2 is only indicating that the kernel can support dual cores.

Doesn't that boil down to the same thing if you **do** have a dual core CPU?

---

### Post by zgornel on 2006-11-27
> **qamelian said:**
> This isn't quite accurate. I get the #2 and I am not using a dual core CPU. I think the #2 is only indicating that the kernel can support dual cores. The SMP part shows that you are runing a SMP kernel, #1 or #2 shows the number of CPUs. On a Pentium4 with Hyperthreading support it also shows 2 CPUs/cores.

---

### Post by muep on 2006-11-27
I don't know if this is because I am using Fedora, but 'uname -a' shows me #1 even though I have a Core 2 Duo and both of the cores are recognized correctly.

cat /proc/cpuinfo is a better way to check the cores.

To the original poster:
You are running a basic kernel with no support for multiple cores. There is a kernel more suited for modern machines, which can be installed with:

sudo apt-get install linux-generic

This solve the problem. After the installation, reboot the copmuter. Then check the output of

cat /proc/cpuinfo

and see if you have lists of information for both of the cores.

---

### Post by steve.horsley on 2006-11-27
Oops - meant to hit cancel, not submit.

---

### Post by civilian on 2006-11-28
When I try to do this I always get the same result which is: screen(s) found but failed to initialized, so I'm close to give up on it.

---

### Post by webjames on 2006-11-28
this is my CPU info and attached is a screen shot of system monitor

NOTE access cpu info type:

```
cat /proc/cpuinfo
```

here is what it says:

> processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      : Intel(R) Pentium(R) 4 CPU 3.20GHz
stepping        : 3
cpu MHz         : 2800.000
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl est cid cx16 xtpr
bogomips        : 6408.08

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      : Intel(R) Pentium(R) 4 CPU 3.20GHz
stepping        : 3
cpu MHz         : 2800.000
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl est cid cx16 xtpr
bogomips        : 6466.20



don't know if this does help, but i hope so. mine is an intel P4 with HT

regards,

James

---

### Post by diepruis on 2006-11-29
> **civilian said:**
> When I try to do this I always get the same result which is: screen(s) found but failed to initialized, so I'm close to give up on it.

I'm assuming you are talking about installing a new kernel. The solution to your problem is easy: you need to install the kernel modules for your graphics card. Have a look around the forums, you should find some help.

---

### Post by noodles_x on 2006-11-30
With cat /proc/cpuinfo I get
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2500  @ 2.00GHz
stepping        : 8
cpu MHz         : 1000.000
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc up pni monitor vmx est tm2 xtpr
And with uname -a
Linux laptop 2.6.17-10-386 #2 Fri Oct 13 18:41:40 UTC 2006 i686 GNU/Linux
In device manager it's Unknown.
I have edgy. What should I do? Processor is mobile duo core t2500
thanks

---

### Post by diepruis on 2006-11-30
> **noodles_x said:**
> Linux laptop 2.6.17-10-386 #2 Fri Oct 13 18:41:40 UTC 2006 i686 GNU/Linux
In device manager it's Unknown.
I have edgy. What should I do? Processor is mobile duo core t2500
thanks

Try

```

sudo apt-get update
sudo apt-get install linux-686-smp

```

Reboot and choose the new kernel from your GRUB boot list (you may have to press ESC during the boot sequence - look for a prompt).

Then try /proc/cpuinfo again.

---

### Post by insane_alien on 2006-11-30
seeing as its handled pretty much the same way as multiple processors and the linux kernel is on pretty much every server(which usually have multiple cpu's) and even a couple of super computers i would say it can handle them just fine.

---

### Post by noodles_x on 2006-11-30
thanks for the advice. It work's now. I just don't understand why 
cpu MHz 1000,it should be 2000. Maybe because it's mobile it changes MHz depending on how much you need...
thanks

---

### Post by compmodder26 on 2006-11-30
Your CPU is being throttled to conservere energy.  It will only go up to the maximum speed if it needs to.  So no worries there.

---

### Post by jdong on 2006-11-30
If you are using Edgy Eft (6.10), Ubuntu is configured out-of-the-box to fully take advantage of your multi-core CPUs. In addition, Ubuntu's scheduler is aware of CPU groups. It will try to keep processes scheduled to groups of CPU's that share a cache (i.e. think if you have 2 dual-core's that share a pair of L2 caches). No further configuration is needed on your part.

If you are using Dapper Drake (6.06LTS), you will need to install the "linux-686" package via Synaptic or apt-get in order to activate more than one core. Dapper Drake's kernel is not CPU group aware, so if you are running Intel Core processors (with shared L2 cache), you will get a slight performance boost from upgrading to Edgy.

In both releases, hyperthreading is turned off by default because of a hardware security weakness in Intel's HT implementation (plus HT really doesn't help much in terms of performance or latency anyway, according to most benchmarks). You need to pass 'ht=on' to the kernel to activate hyperthreading if you so choose, but you should be aware what kind of security issues you might be opening yourself to.

---

### Post by Lord Illidan on 2006-11-30
> **insane_alien said:**
> seeing as its handled pretty much the same way as multiple processors and the linux kernel is on pretty much every server(which usually have multiple cpu's) and even a couple of super computers i would say it can handle them just fine.

Just a couple of supercomputers??? More than just a couple...Linux can handle dual core far far better than Windows.

---

### Post by pillu on 2006-11-30
Hi all,

Being the original poster of this thread I am slightly embarrased not to have followed up on the suggestions for almost a week - was too busy. But here is what I did :
```
sudo apt-get update
sudo apt-get install linux-686-smp
```

I saw that it installed the linux-restricted-modules-686 automatically. So didn't need to install that separately. On booting into this new kernel here is what I get
```
anand@zorg:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz
stepping        : 6
cpu MHz         : 1662.547
cache size      : 2048 KB
physical id     : 0
siblings        : 1
core id         : 255
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm pni monitor ds_c pl est tm2 cx16 xtpr lahf_lm
bogomips        : 3329.70

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz
stepping        : 6
cpu MHz         : 1662.547
cache size      : 2048 KB
physical id     : 1
siblings        : 1
core id         : 255
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm pni monitor ds_c pl est tm2 cx16 xtpr lahf_lm
bogomips        : 3329.70

```

So I guess the 2 cores are now recognized. But the device manager still shows that the processor is unrecognized. So I guess that is not the best way to check the status. Also system monitor now shows the status of two cpus which is good. One last thing
```
anand@zorg:~$ uname -a
Linux zorg 2.6.15-27-686 #1 SMP PREEMPT Sat Sep 16 02:13:27 UTC 2006 i686 GNU/Li nux

```
uname -a still shows #1. So this shows that you do not need to have a #2 for both kernels to be recognized. 

Thanks for all the help on this folks. The really cool thing about the kernel install was that it retained all my settings from my last desktop. I was dreading that I would have to redo my beautiful gnome desktop again.

Cheers

---

### Post by jdong on 2006-11-30
The "#1" is a part of the kernel version string. It has nothing to do with how many CPU's are being recognized :)

---

### Post by diepruis on 2006-12-01
Thanks for clearing that up, jdong.

---

### Post by flyingsolo on 2006-12-04
Having read this thread, I am still a little confused.  I understand Edgy is configured to automatically recognize and employ dual cores whereas Dapper requires updating to the 686-smp kernel.  However, my core2duo is running Edgy and cat /proc/cpuinfo shows one core at 1000 MHz and uname -a shows:
2.6.17-10-386 #2 Fri Oct 13 18:41:40 UTC 2006 i686 GNU/Linux

So, do I have to do the sudo apt-get update and sudo apt-get install linux-686-smp and why, if Edgy was supposed to "automatically" recognize the two cores?

(not that this is difficult to do, I just think it is misleading to newcomers)

Edit:  after sudo apt-get install linux-686-smp I get the message that I already have the newest version but still I don't seem to have both cores recognized, as below:
cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz
stepping        : 6
cpu MHz         : 1000.000
cache size      : 4096 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc up pni monitor ds_cpl vmx est tm2 cx16 xtpr lahf_lm
bogomips        : 3995.11

Can anyone explain please?

---

### Post by jdong on 2006-12-04
Your system is still using the 386 kernel for some reason. The new Edgy general kernel flavor is known as -generic, which supports all flavors of processors, SMP or not.

Can you try **sudo apt-get install linux-generic**?

---

### Post by flyingsolo on 2006-12-04
> **jdong said:**
> Your system is still using the 386 kernel for some reason. The new Edgy general kernel flavor is known as -generic, which supports all flavors of processors, SMP or not.

Can you try **sudo apt-get install linux-generic**?

Well, I did as suggested but cpuinfo is the same--no change.  Suggestions?

EDIT--Fixed!  Small oversight; I just had to reboot and "generic" kernel was in selection list of grub (makes me wonder if it was always there & I kept picking the 1st in list which was 386 kernel!)
So..one more question; how to change order of kernels in grub such that this is now the default selection for automatic boot?  Probably this is addressed elsewhere in forums & I'll have a look.  Thanks jdong.

---

### Post by jdong on 2006-12-04
> **flyingsolo said:**
> Well, I did as suggested but cpuinfo is the same--no change.  Suggestions?

EDIT--Fixed!  Small oversight; I just had to reboot and "generic" kernel was in selection list of grub (makes me wonder if it was always there & I kept picking the 1st in list which was 386 kernel!)
So..one more question; how to change order of kernels in grub such that this is now the default selection for automatic boot?  Probably this is addressed elsewhere in forums & I'll have a look.  Thanks jdong.

Use Synaptic to remove linux-image-386 and all its associated packages from your system.

---

### Post by psych-major on 2006-12-07
No, if they were, you would see a second listing for processor 1:
```
DSI9600-42299:~ # cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      :                   Intel(R) Xeon(TM) CPU 2.80GHz
stepping        : 3
cpu MHz         : 2793.141
cache size      : 2048 KB
physical id     : 0
siblings        : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx lm pni monitor ds_cpl cid cx16 xtpr
bogomips        : 5505.02
clflush size    : 64
cache_alignment : 128
address sizes   : 36 bits physical, 48 bits virtual
power management:


processor       : 1
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      :                   Intel(R) Xeon(TM) CPU 2.80GHz
stepping        : 3
cpu MHz         : 2793.141
cache size      : 2048 KB
physical id     : 3
siblings        : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx lm pni monitor ds_cpl cid cx16 xtpr
bogomips        : 5570.56
clflush size    : 64
cache_alignment : 128
address sizes   : 36 bits physical, 48 bits virtual
power management:
```

I'm having the same issue, BTW.

---

### Post by jdong on 2006-12-07
What problem are you having?

---

### Post by diepruis on 2006-12-07
To psych-major:

I believe you are misunderstanding. You expect two listing below CPU1, but in fact the two listings have been giving already. CPU1 is your second CPU, while CPU0 at the start is your first core.

If I misunderstood your post, I apologise.

---

