---
title: "[SOLVED] Enabling CPU Freq. scaling on AMD Athlon XP 2200+"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by isaacj87 on 2007-09-24
Hey guys,

Just fully switched my parents over to ubuntu! :) But one problem....CPU freq scaling is "unsupported"

It's an AMD Athon (XP) 2200+ and it's running at full performance. Can anyone tell me how to enable CPU freq so I can turn on "Ondemand?"

Thanks!

---

### Post by Maestro23 on 2007-09-24
Check the following section in the Feisty Starter's Guide: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_your_CPU.27s_Power_Saving.2FFrequency_Scaling_features](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_your_CPU.27s_Power_Saving.2FFrequency_Scaling_features)

Hope it helps.

---

### Post by isaacj87 on 2007-09-24
Thanks for the quick reply. But within the 2nd step I get this error:

```

siti@siti-desktop:~$ sudo modprobe powernow-k7
FATAL: Error inserting powernow_k7 (/lib/modules/2.6.20-16-generic/kernel/arch/i386/kernel/cpu/cpufreq/powernow-k7.ko): No such device

```

---

### Post by w4ett on 2007-09-24
I don't believe (I could be wrong though) that the Athlon XP is capable of scaling.......You'll need an Athlon XP-M  for that.

---

### Post by Maestro23 on 2007-09-24
> **isaacj87 said:**
> Thanks for the quick reply. But within the 2nd step I get this error:

```

siti@siti-desktop:~$ sudo modprobe powernow-k7
FATAL: Error inserting powernow_k7 (/lib/modules/2.6.20-16-generic/kernel/arch/i386/kernel/cpu/cpufreq/powernow-k7.ko): No such device

```

Did you try the commands under (Others-Unknown)

*w4ett my be right, if those commands don't work.

---

### Post by isaacj87 on 2007-09-24
> **w4ett said:**
> I don't believe (I could be wrong though) that the Athlon XP is capable of scaling.......You'll need an Athlon XP-M  for that.

So what should I do? When I add the CPU freq applet to the panel it says "1.8 ghz (100%)" Isn't that bad and wouldn't my cpu burn out?

---

### Post by w4ett on 2007-09-24
1.8 Ghz is the rated speed of that CPU

---

### Post by isaacj87 on 2007-09-24
> **w4ett said:**
> 1.8 Ghz is the rated speed of that CPU

Sorry, I'm not familiar with these things. So if I don't have CPU freq scaling this isn't necessarily a bad thing...

---

### Post by Maestro23 on 2007-09-24
> **isaacj87 said:**
> Sorry, I'm not familiar with these things. So if I don't have CPU freq scaling this isn't necessarily a bad thing...

Did you try the commands for Unknown-Other CPU's?

---

### Post by isaacj87 on 2007-09-24
> **Maestro23 said:**
> Did you try the commands for Unknown-Other CPU's?

Yeah, didn't work either...:(

---

### Post by isaacj87 on 2007-09-24
What about the alterntive-CD. Do you guys think that if I install with that maybe I might have CPU freq scaling?

The biggest concern I have is my comp burning out. If there really isn't any problem then I'll just leave it as is.

---

### Post by w4ett on 2007-09-24
> **isaacj87 said:**
> Sorry, I'm not familiar with these things. So if I don't have CPU freq scaling this isn't necessarily a bad thing...

CPU Scaling is used on mobile devices (Laptops and Tablet PCs) to reduce power usage and prolong battery life.  On a desktop (unless you are running a low power box) it serves no purpose.

---

### Post by adamklempner on 2007-09-24
Right.  I believe that the multiplier is locked on most regular athlons, so frequency scaling won't work anyway.  Just leave it as it is.  Nothing is wrong.

---

### Post by Maestro23 on 2007-09-24
> **adamklempner said:**
> Right.  I believe that the multiplier is locked on most regular athlons, so frequency scaling won't work anyway.  Just leave it as it is.  Nothing is wrong.

Been doing some googling, and this is the conclusion I'm coming to about the OP's cpu.

---

### Post by isaacj87 on 2007-09-24
Sounds good guys....Thanks for all the help! :)

---

### Post by LowSky on 2007-09-24
All scaling does is allow the chip to use a lower clock rate for lower batery consumption.

Desktop processors do not need this feature because the have constant power.Only the Mobile version of an Athlon will have this feature, also the motherboard has to support it under the Bios As well.

---

