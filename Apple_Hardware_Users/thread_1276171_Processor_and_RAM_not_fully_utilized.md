---
title: "Processor and RAM not fully utilized?"
date: 2009-09-26
forum: Apple Hardware Users
---

### Post by WindPower on 2009-09-26
Hello,
I have a MacBook Pro 5,3 (The 15-inch, 2.8 GHz model) bought a few weeks ago and have installed Kubuntu 9.04 64-bit on it. Yet, sysinfo says this:
> CPU information: Intel(R) Core(TM)2 Duo CPU     T9600  @ **2.80GHz**
Frequency: **1596.000 MHz** (Shouldn't this be ~2800 MHz?)

Memory total: **3614 MiB** (Shouldn't this be 4,096 MiB?)
Is the hardware not being recognized properly? :(

---

### Post by Bachstelze on 2009-09-26
For the CPU, there is probably some frequency scaling in effect. For the RAM, you can't use 4 GB of RAM on a 32 bit OS (because 4G > 2^32).

---

### Post by WindPower on 2009-09-26
> **Bachstelze said:**
> For the CPU, there is probably some frequency scaling in effect. For the RAM, you can't use 4 GB of RAM on a 32 bit OS (because 4G > 2^32).

I am on AC power and have selected the "Performance" CPU scaling policy. As said in the first post, I installed Kubuntu 64-bit on it.

---

### Post by Ravernomina on 2009-09-28
I have the same problem my friend... If you got the NVIDIA 9400M or NVIDAI 9600 Its just some of your RAM is devoted to the Graphics card 250MB of it.
So this is normal it happens to me 2. Even In snowleopard as well O:

---

### Post by WindPower on 2009-09-28
> **Ravernomina said:**
> I have the same problem my friend... If you got the NVIDIA 9400M or NVIDAI 9600 Its just some of your RAM is devoted to the Graphics card 250MB of it.
So this is normal it happens to me 2. Even In snowleopard as well O:Wait, what? I paid the extra cost to have the 512 MB version of the 9600M GT rather than the default 256 MB 9600M GT. Does that mean I paid the extra cost only to have an extra 256 MB of my RAM reserved for graphics? If so, I'm so getting my money back ](*,)

What about the processor frequency though?

---

### Post by WindPower on 2009-09-29
Bump.
Here are some screenshots, if it helps...
[img]http://img205.imageshack.us/img205/6608/screenshot1jb.png[/img]
[img]http://img205.imageshack.us/img205/626/screenshot2w.png[/img]

---

### Post by the_squircle on 2009-09-29
I know from experience on my MBP that if I get close to 100% of the scaled speed, it scales up to the full (2.4GHz in my case). And the extra cost was for a faster 8600M GT (rev A i believe), and for it to take 512 MB of your internal memory.

---

### Post by WindPower on 2009-09-29
> **the_squircle said:**
> I know from experience on my MBP that if I get close to 100% of the scaled speed, it scales up to the full (2.4GHz in my case). And the extra cost was for a faster 8600M GT (rev A i believe), and for it to take 512 MB of your internal memory.

You are right for the CPU, I ran some benchmarks using HardInfo and it rates my CPU between a dual-core 2.33 GHz and a dual-core 2.66 GHz. Still not quite 2.8 GHz but at least it's not 1.6 GHz :) And I guess I could bump that score a bit if I closed some background apps.

Edit: Indeed, I even surpassed the 2.8 GHz mark! :D Marking thread as half-solved.

As for the graphics card, it's an NVIDIA 9600M GT with the "512 MB of video memory" option.

I checked in OS X and I indeed do not have 4 GB either! :( It says I have 3.75 GB in the Activity Monitor, and the System Profiler says I have 2 sticks of 2 GB of RAM each. If I di have 3.75 GB of RAM in OSX, that would mean there's 256 MB left for video memory... But I have 512 MB of video memory according to nvidia-settings...?

I'm kind of lost among all this memory stuff :confused:

---

### Post by the_squircle on 2009-09-29
> **WindPower said:**
> You are right for the CPU, I ran some benchmarks using HardInfo and it rates my CPU between a dual-core 2.33 GHz and a dual-core 2.66 GHz. Still not quite 2.8 GHz but at least it's not 1.6 GHz :) And I guess I could bump that score a bit if I closed some background apps.

Edit: Indeed, I even surpassed the 2.8 GHz mark! :D Marking thread as half-solved.

As for the graphics card, it's an NVIDIA 9600M GT with the "512 MB of video memory" option.

I checked in OS X and I indeed do not have 4 GB either! :( It says I have 3.75 GB in the Activity Monitor, and the System Profiler says I have 2 sticks of 2 GB of RAM each. If I di have 3.75 GB of RAM in OSX, that would mean there's 256 MB left for video memory... But I have 512 MB of video memory according to nvidia-settings...?

I'm kind of lost among all this memory stuff :confused:

The 512MB 8600M GT has 256MB of dedicated video memory. Otherwise, the configuration is exactly the same as the 256MB 8600M GT.

---

