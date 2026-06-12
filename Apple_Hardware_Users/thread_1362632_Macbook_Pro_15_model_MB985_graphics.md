---
title: "Macbook Pro 15 model MB985 graphics"
date: 2009-12-23
forum: Apple Hardware Users
---

### Post by dogturd on 2009-12-23
Hi,

I'm looking at the 2.66GHz MacBook Pro (MB985*/A) which is the middle of the range of the 15" Macbooks. It does however have 2 graphics chipsets. 

"NVIDIA GeForce 9600M GT graphics processor; and NVIDIA GeForce 9400M graphics processor with 256MB of DDR3 SDRAM shared with main memory"

Has anyone installed 9.10 on this model laptop? Whats the situation regarding driver and usability on this model with the Nvidia graphics chipset?

Thanks

---

### Post by alexmurray on 2009-12-23
Unless you boot via EFI (which is non-trivial - see [this thread]("http://ubuntuforums.org/showthread.php?t=995704") for more info) you can only use the 9600MGT (same as under Windows if you dual boot using Bootcamp). The nvidia-glx-185 driver (provided by Ubuntu) is perfectly stable for me on my MBP5,1 with the 9600MGT.

---

### Post by Seq on 2009-12-24
> **alexmurray said:**
> Unless you boot via EFI (which is non-trivial - see [this thread]("http://ubuntuforums.org/showthread.php?t=995704") for more info) you can only use the 9600MGT (same as under Windows if you dual boot using Bootcamp). The nvidia-glx-185 driver (provided by Ubuntu) is perfectly stable for me on my MBP5,1 with the 9600MGT.

I'd elaborate and say the nvidia driver is as stable and featureful as the nvidia driver gets, which leaves a bit to be desired (coming from a former -intel user here).

If you update the driver and don't rebot (or stop X, remove and insert nvidia module, start X) then you're risking an X crash. It seems to run rather hot -- wish we could switch to that 9400 :(

---

### Post by dogturd on 2009-12-24
Thanks for the info and advice.

---

