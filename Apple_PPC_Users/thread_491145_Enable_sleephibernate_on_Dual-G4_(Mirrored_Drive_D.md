---
title: "Enable sleep/hibernate on Dual-G4 (Mirrored Drive Door) wiht Feisty?"
date: 2007-07-03
forum: Apple PPC Users
---

### Post by jbrax on 2007-07-03
Has anyone succeeded enabling sleep - hibernate with Dual-G4 PowerPC (Mirrored Drive Door) and Ubuntu Feisty? 

Sleep worked out of the box with iBook G3 and iMac G3, but with this Dual-G4 I only get a locked screensaver. 

/var/log/messages: 
gnome-power-manager: power-pmu : PMU_IOC_SLEEP failed   org.freedesktop.Hal.Device.SystemPowerManagement.No
tSupported code='32' quark='g-exec-error-quark'
gnome-power-manager: suspend failed
gnome-power-manager: cannot hibernate as not allowed from policy
gnome-power-manager: hibernate failed

uname -a
Linux ratamo 2.6.20-16-powerpc-smp #3 SMP Thu Jun 7 19:36:12 UTC 2007 ppc GNU/Linux

dmesg | grep pmu
[    0.000000] via-pmu: Server Mode is disabled
[   27.965009] PMU i2c /pci@f2000000/mac-io@17/via-pmu@16000/pmu-i2c
[   35.695613] PowerMac i2c bus pmu 2 registered
[   35.695711] PowerMac i2c bus pmu 1 registered

dmesg | grep apm
[   56.087440] apm_emu: APM Emulation 0.5 initialized.

/proc/cpuinfo:
processor       : 0
cpu             : 7455, altivec supported
clock           : 866.666664MHz
revision        : 0.1 (pvr 8001 0201)
bogomips        : 66.56
processor       : 1
cpu             : 7455, altivec supported
clock           : 866.666664MHz
revision        : 0.1 (pvr 8001 0201)
bogomips        : 66.56
total bogomips  : 133.12
timebase        : 33303869
platform        : PowerMac
machine         : PowerMac3,6
motherboard     : PowerMac3,6 MacRISC2 MacRISC Power Macintosh
detected as     : 129 (PowerMac G4 Windtunnel)
pmac flags      : 00000010
L2 cache        : 256K unified
pmac-generation : NewWorld

/proc/pmu/info:
PMU driver version     : 2
PMU firmware version   : 0c
AC Power               : 1
Battery count          : 0

/proc/pmu/interrupts:
  0:          0 (Total CB1 triggered events)
  1:          0 (Total GPIO1 triggered events)
  2:          0 (PC-Card eject button)
  3:          0 (Sound/Brightness button)
  4:          0 (ADB message)
  5:          0 (Battery state change)
  6:          0 (Environment interrupt)
  7:          0 (Tick timer)
  8:          0 (Ghost interrupt (zero len))
  9:          1 (Empty interrupt (empty mask))
 10:          0 (Max irqs in a row)

/proc/pmu/options:
server_mode=0

Some thread with the same unanswered question:
[http://ubuntuforums.org/showthread.php?t=262261&highlight=hibernate](http://ubuntuforums.org/showthread.php?t=262261&highlight=hibernate)

dmesg attached

---

### Post by stmiller on 2007-07-03
Sleep or hibernate only works with machines with ATI cards, Powermacs included. I believe that it is possible to hack nvidia machines so they sleep, but then they will not wake up- according to some chatting I did with Gentoo PPC folks. Sorry.  :-(  Perhaps try to find a cheap Radeon card.

---

