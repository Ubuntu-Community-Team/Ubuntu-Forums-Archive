---
title: "Fractalize VMWare - VMware install to physical partion plus dualboot possible?"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by effgee on 2007-01-23
So, I'm running here in my Windows XP installation, I have an Ubuntu install in a virtual machine that works fantastic. This vmware is using the** physical partitions on my 3rd disk.**

If I reboot, and tell my bios to **boot from the disk that has the Ubuntu partion, **I get the loader screen of Ubuntu, I can choose from the kernel, kernel-safe and memtest.
If I proceed from there it halts.


**Herein lies the Difficulty: I** have an ATI X1300 card, and unluckily for me, it is one of the defective / bugged units that has graphics corruption issues in Dos modes. Including the grub screen. 
Usually, when I get to framebuffer mode it is fine, but at the moment, when I select a kernel, the errors that are onscreen ( if any) are lost in gibberish. So, what should / can I do in my booted vmware environment to fix grub and have it boot properly when I wish to dualboot.

This may be a difficult question but I would appreciate help.

---

### Post by Bachstelze on 2007-01-23
When you install an OS in VMware, it is configured to use the hardware of your virtual machine. So when you boot it from your real machine, with your real hardware, there's simply no way it can work.

---

