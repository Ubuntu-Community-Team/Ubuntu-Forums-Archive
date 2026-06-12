---
title: "amd64 noapic kernal panic"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by dimnullspace on 2007-02-07
Had to install alternate install DVD *6.10.amd64.iso with ‘apic=off’ and ‘noapic’ in text mode. 

Install went all the way, but now when I try to boot off HDD I get the same kernel panic error which I thought I solved by installing with boot: kernel …….stuff…… apic=off noapic

Q1: is apic=off equivalent to noapic

Q2: When I boot it goes straight to kernel panic. How do I boot off HDD in rescue? Or how do I add boot kernel pars apic=off and noapic when I boot off HDD. 

Q3: not sure if this noapic stuff is the fix anyways becuase I still  can not boot the live CD with the kernal pars noapic and apic=off? system hangs for ever.

My OEM: ASUS M2N32-SLI-D, AMD64 +3800 Dual Core, CORSAIR XMS2 240-Pin DDR2 800, NVIDIA GeForce 7300 GT, HDD WD 150G Raptor

The problem is discussed here.
[http://www.ubuntuforums.org/showthread.php?t=258298&highlight=noapic](http://www.ubuntuforums.org/showthread.php?t=258298&highlight=noapic)
[http://www.ubuntuforums.org/showthread.php?t=334083&highlight=noapic](http://www.ubuntuforums.org/showthread.php?t=334083&highlight=noapic)

---

### Post by Quintin Riis on 2007-02-07
Hit the esc key when booting to bring up the GRUB menu.

---

### Post by dimnullspace on 2007-02-07
Fixed-

Had to flash bios to Rev 0903 per [www.asus.com](www.asus.com) M2N32SLI-D

Seems ASUS has fixed the linux compatability issues IO-APIC error: MP-BIOS bug 8254 timer not connected to IO-APIC

If you get this error on an ASUS M-board you may need to flash your bios, but only if you know what you are doing. That is, do your HW before you flash bios.

aha

---

