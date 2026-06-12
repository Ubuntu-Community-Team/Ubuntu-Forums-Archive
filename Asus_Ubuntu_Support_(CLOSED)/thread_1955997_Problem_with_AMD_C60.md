---
title: "Problem with AMD C60"
date: 2012-04-10
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Normal01 on 2012-04-10
Hey all,
I have an Asus 1215b with AMD C60, but Ubuntu recognizes the AMD C60 as an AMD C50. In fact, if I write
```
cpufreq-info
```
on the terminal, it says me that the CPU goes from 800mhz to 1ghz, instead of 1,33ghz.

Could anybody help me?

Thanks a lot

---

### Post by linlinas on 2012-05-15
I am having the same issue, it looks like ubuntu 12.04 doesn't recognize turbo core on c60.
 Any thoughts? please ....

---

### Post by linlinas on 2012-05-15
> **linlinas said:**
> I am having the same issue, it looks like ubuntu 12.04 doesn't recognize turbo core on c60.
 Any thoughts? please ....

I post my cpufreqd-info below

# cpufreq-info
cpufrequtils 007: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to [email]cpufreq@vger.kernel.org[/email], please.
analyzing CPU 0:
  driver: powernow-k8
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 1000 ns.
  hardware limits: 800 MHz - 1000 MHz
  available frequency steps: 1000 MHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 800 MHz and 800 MHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz (asserted by call to hardware).
  cpufreq stats: 1000 MHz:0.49%, 800 MHz:99.51%  (1)
analyzing CPU 1:
  driver: powernow-k8
  CPUs which run at the same hardware frequency: 1
  CPUs which need to have their frequency coordinated by software: 1
  maximum transition latency: 1000 ns.
  hardware limits: 800 MHz - 1000 MHz
  available frequency steps: 1000 MHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 800 MHz and 800 MHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz (asserted by call to hardware).
  cpufreq stats: 1000 MHz:0.49%, 800 MHz:99.51%  (1)

---

### Post by deport on 2012-05-18
I'm also having trouble with Ubuntu 12.04 and an AMD Turion dual core processor.
The PC seems to run much slower than it should as a dual core.  
It may also be consuming more electricity than needed.
I thought that code AMD provided for OS writers taking advantage of the chip had already been a part of older Linux kernels.  Maybe some of the AMD code was removed?

dmesg gives many powernow-k8 errors, some repeated, including

powernow-k8: transition frequency failed
failing targ, change pending bit set
pending bit very stuck
error - out of sync
ph2 null fid transition

---

### Post by antiplex on 2012-06-04
> **Normal01 said:**
> Hey all,
I have an Asus 1215b with AMD C60, but Ubuntu recognizes the AMD C60 as an AMD C50. In fact, if I write
```
cpufreq-info
```
on the terminal, it says me that the CPU goes from 800mhz to 1ghz, instead of 1,33ghz.

Could anybody help me?

Thanks a lot

hello normal01,

how do you exactly know that ubuntu sees your cpu as a c50? does it say so somewhere? in my case, running ```
dmesg | grep CPU0
``` tells me the correct cpu type: ```
[    0.083400] CPU0: AMD C-60 APU with Radeon(tm) HD Graphics stepping 00
```you probably base that assumption on the fact that you can't choose the promised 1,33ghz **turbo** clock speed?
if so, this seems to be a general misbelief of how amd's (as well as intel's) turbo technology works. in fact, you can't set the tubo frequency manually and the cpu also announces its regular clock speeds to the system **but** in cases where the thermal specification (TDP 9W) permits the cpu raises its clock speed internally as long as it can before it drops back to the safe waters of the regular speeds. as a matter of fact, the turbo-frequency is not displayed as such and for the user, it might just appear as if the cpu is running on its highest nominal clock speed.
note that in order to follow the thermal specs some cpu's might enter turbo e.g. only when only one core is under load and the other can enter some light sleep state.
there is a really nice cpu information utility for windows called cpuz but i can't recall if this is able to determine when exactly the cpu enters and exits turbo mode.

so the bootom line here seems to me that your cpu is probably fine and ubuntu is doing a great job getting as much as possible out of your hardware that might clock at 1,33 ghz more often than you would think ;)

have a nice day,
regards,
anti

---

### Post by deport on 2012-06-12
> **antiplex said:**
> hello normal01,

how do you exactly know that ubuntu sees your cpu as a c50? does it say so somewhere? in my case, running ```
dmesg | grep CPU0
``` tells me the correct cpu type: ```
[    0.083400] CPU0: AMD C-60 APU with Radeon(tm) HD Graphics stepping 00
```you probably base that assumption on the fact that you can't choose the promised 1,33ghz **turbo** clock speed?
if so, this seems to be a general misbelief of how amd's (as well as intel's) turbo technology works. in fact, you can't set the tubo frequency manually and the cpu also announces its regular clock speeds to the system **but** in cases where the thermal specification (TDP 9W) permits the cpu raises its clock speed internally as long as it can before it drops back to the safe waters of the regular speeds. as a matter of fact, the turbo-frequency is not displayed as such and for the user, it might just appear as if the cpu is running on its highest nominal clock speed.
note that in order to follow the thermal specs some cpu's might enter turbo e.g. only when only one core is under load and the other can enter some light sleep state.
there is a really nice cpu information utility for windows called cpuz but i can't recall if this is able to determine when exactly the cpu enters and exits turbo mode.

so the bootom line here seems to me that your cpu is probably fine and ubuntu is doing a great job getting as much as possible out of your hardware that might clock at 1,33 ghz more often than you would think ;)

have a nice day,
regards,
anti

I can't speak for the original poster, but in my case with a Turion 64 X2 there are errors reported by the kernel.  The CPU is correctly identified, but Ubuntu throws numerous errors with dmesg because Ubuntu doesn't know how to handle AMD power scheme.  I get powernow-k8 "failing targ", "transition frequency failed", "error - out of sync", "Hardware error - pending bit very stuck" repeated many times.

I don't know where to report this, but I think the result is that either power is wasted, or Ubuntu runs more sluggish than it should on the hardware.

---

### Post by Normal01 on 2012-07-06
Thank you so much antiplex  !!! I'm sorry if I answer now. 
However, you have right, if i wrote these code on terminal, it show me 
```
[    0.075693] CPU0: AMD C-60 APU with Radeon(tm) HD Graphics stepping 00
```
I thought that Ubuntu doesn't recognize AMD-C60 because I can't choose the turbo clock speed! Thank you very much for explanation!
Bye
:D

---

### Post by Normal01 on 2012-07-07
[QUOTE=Normal01;11833159]Hey all,
I have an Asus 1215b with AMD C60, but Ubuntu recognizes the AMD C60 as an AMD C50. In fact, if I write
```
cpufreq-info
```
on the terminal, it says me that the CPU goes from 800mhz to 1ghz, instead of 1,33ghz.

Could anybody help me?

Thanks a lot

---

