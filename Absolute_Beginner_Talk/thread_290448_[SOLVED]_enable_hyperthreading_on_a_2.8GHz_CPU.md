---
title: "[SOLVED] enable hyperthreading on a 2.8GHz CPU"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by niki001 on 2006-11-01
Hi all,

Im working severall weeks with Kubuntu now and I'm starting to feel at home with it. I've installed some eyecandy and my system is getting pretty slow because of that. So now I want to speed things up. 
I've got a 2.8Ghz CPU with hyperthreading, HT is enabled via BIOS.
For the moment I'm using the 2.6.15-27-386 kernel so my HT isn't supported.
I recently installed the 686-smp kernel to be able to use my HT.
In grub I added the ht=on option.
When I boot into the SMP kernel I get the following message:
'error: only one processor found' then it reboots.:-k. Starting up in recovery mode gives the same result.

Can anybody help me on this pleas?

thx

---

### Post by hellodotcom on 2006-11-01
how do i post Replys :confused: ](*,) :confused:

---

### Post by unisol on 2006-11-01
my understanding is you have a single processor install the original kernel or if it is still in grub boot from it.there have to be some other tweaks you can use to speed up your system. can you give system specs?

---

### Post by niki001 on 2006-11-01
Indeed I have a single proc but with HT possibility. As far as i understood from other threads i need to install the 686-smp kernel to be able to activate HT. I'm still able to boot in my origanal kernel (but this one is getting kinda slow, and ht isn't enabled).

These are some of my settings, do you need other info?

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Pentium(R) 4 CPU 2.80GHz
stepping        : 9
cpu MHz         : 2793.367
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
bogomips        : 5679.20

---

### Post by jhenager on 2006-11-01
> **niki001 said:**
> Hi all,

Im working severall weeks with Kubuntu now and I'm starting to feel at home with it. I've installed some eyecandy and my system is getting pretty slow because of that. So now I want to speed things up. 
I've got a 2.8Ghz CPU with hyperthreading, HT is enabled via BIOS.
For the moment I'm using the 2.6.15-27-386 kernel so my HT isn't supported.
I recently installed the 686-smp kernel to be able to use my HT.
In grub I added the ht=on option.
When I boot into the SMP kernel I get the following message:
'error: only one processor found' then it reboots.:-k. Starting up in recovery mode gives the same result.

Can anybody help me on this pleas?

thx
I found this on another forum, and it seems you have installed the correct kernel.
"Right, a Unix kernel needs to be SMP-enabled for a system to "recognize" the 2nd CPU (and any application, incl. BOINC to use it). I don't use Gentoo but found this:

Gentoo SMP kernel discussion [http://www.linuxforums.org/forum/gentoo-linux-help/58899-smp-kernel-not-installed.html](http://www.linuxforums.org/forum/gentoo-linux-help/58899-smp-kernel-not-installed.html)

As others pointed out, in today's user-friendly systems, there's usually a "package" that installs the SMP-enabled kernel, e.g. for Debian (and Debian-derivative Ubuntu):


    # apt-cache search smp
    kernel-image-2.6.8-12-amd64-k8-smp - Linux kernel image for version 2.6.8 on AMD64 SMP systems
    kernel-image-2.6.8-12-em64t-p4-smp - Linux kernel image for version 2.6.8 on Intel EM64T SMP systems
    kernel-image-2.6.8-3-686-smp - Linux kernel image for version 2.6.8 on PPro/Celeron/PII/PIII/P4 SMP.



and you'd use something like


    # apt-get install kernel-image-2.6.8-...



to install it, reboot and you're done.

But, if a CPU is HT (HyperThreaded) rather than "true" dual-core, then the performance diff is small and you might not want to bother with it (unless you like tweaking)"

I also found an article that says the performance increase should be about 1.15 to 1.3 X the performance without hyperthreading enabled.
Hope this sheds a little light on your issue.

---

### Post by Cynical on 2006-11-01
The smp kernel is for multiple processors or dual-core processors. Hyperthreading is essentially just pretending you have two processors. What you should do is follow [this](http://ubuntuforums.org/showthread.php?t=217657&highlight=kernel.org) guide to get the latest kernel and enable hyperthreading for it. That will give you the largest performance improvement.

---

### Post by bollix47 on 2006-11-01
When I was using 686-smp in dapper I never added "HT=on" in grub.  It worked fine without that.  Showed two processors in system monitor.

---

### Post by niki001 on 2007-09-08
Hi people,

cleaning up some threads, found this one not yet marked as solved.
Well, its solved. 
How, simply evolving from edgy to Feisty. Now ive got full capacity from my comp.

great work for the dev. teams!!!

thx

---

