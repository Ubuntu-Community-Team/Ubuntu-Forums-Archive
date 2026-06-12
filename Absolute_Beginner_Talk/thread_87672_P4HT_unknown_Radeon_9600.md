---
title: "P4HT unknown? Radeon 9600?"
date: 2005-11-08
forum: Absolute Beginner Talk
---

### Post by greg_mci on 2005-11-08
I've spent quite a lot of time searching this forum and the whole internet, but i still don't get it.

I got a Pentium 4 Hyperthreading 3.0, but the Device Manager says the processpr was unknown. Why doesn't Breezy recognize the processor? (The same for kernel 386 and 686). Does this result in a lack of performance, as the machine seems to be running quite smoothly (1024 MB Ram)?

The second problem I got:
I installed the new ATI 8.18.06 drivers for my Radeon 9600, but the ATI control panel says OpenGL was unavailable and glxgears keeps saying 1820 frames in 5.2 seconds = 347.241 FPS, I guess that's rather poor. :cool:

Please help me, i just don't want to go back to Windows again...

---

### Post by twisted_steel on 2005-11-08
To answer your first question, the 'unknown' processor should not be a problem. I get the same thing in Device Manager, and I have a 1.8 GHz Pentium M.

---

### Post by jdong on 2005-11-08
UNKNOWN processor is just what your BIOS reports. It's not a big deal.

If you have HT turned on, make sure you run an SMP kernel, which can take advantage of the Hyperthreading functionality. Else, turn off HT altogether at the BIOS level. I've never ever seen any performance improvement coming from HT, but it sure disturbs sensitive 3rd party drivers quite well.,

---

### Post by greg_mci on 2005-11-09
thanks a lot guys.

is there anybody out there who can help me with the graphics problem?

---

### Post by slobberchops on 2005-11-09
[QUOTE=jdong]UNKNOWN processor is just what your BIOS reports. It's not a big deal.

If you have HT turned on, make sure you run an SMP kernel, which can take advantage of the Hyperthreading functionality. Else, turn off HT altogether at the BIOS level. I've never ever seen any performance improvement coming from HT, but it sure disturbs sensitive 3rd party drivers quite well.,[/QUOTE]


That's interesting, because I have HT, enabled in the BIOS, and I think I just noticed a significant performance improvement in xorg when I switched to the NON-SMP kernel.  I am wondering if anyone has heard any issue about HT or SMP kernels and xorg performance in breezy.

I am also unable to get 3d graphics acceleration to work on this laptop, and I think people have reported it working.  I wonder if your remark about it disturbung drivers is signficant.  What kinds of distrurbances are you aware of?

---

### Post by Vorian on 2005-11-09
[QUOTE=greg_mci]thanks a lot guys.

is there anybody out there who can help me with the graphics problem?[/QUOTE]

ATI!!!!!  

Use this how to... It worked for me

[=HERE=]("http://www.ubuntuforums.org/showthread.php?t=75378&highlight=sudo+dpkg-reconfigure+xserver-xorg")

---

### Post by jdong on 2005-11-09
If you're using HT and a SMP kernel, you're using HT.

If you use a non-SMP kernel, you are NOT using HyperThreading, regardless of the BIOS setting.


Often times performance is faster with HT **OFF**, though realtime-level latency may slightly increase (HT is a workaround for pipeline latency problems... Dual-Core is the real solution).

---

