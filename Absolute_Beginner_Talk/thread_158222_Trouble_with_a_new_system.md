---
title: "Trouble with a new system"
date: 2006-04-10
forum: Absolute Beginner Talk
---

### Post by bobpur on 2006-04-10
I am installing Ubuntu v5.10 in a new system. The install went OK, but when it boots up, it stops at "Starting hotplug subsystem." 
  Known specs are; AMD 64 +3000 processor (on a Machspeed Viper motherboard), 1 gb DDR 400 RAM, 200 SATA harddrive with a 20 gb secondary (PATA) harddrive.
  Same thing happens with a Kubuntu v5.10 install. the AMD 64 version of Ubuntu won't install at all.
  I've removed everything but the mouse, monitor and keyboard.
  I'll disconnect the secondary harddrive (possible shunt/cable conflict) and try again.
  Any help would be appreciated.      bobpur

---

### Post by trent dillman on 2006-04-10
try passing 'noapic, nolapic' to grub on boot...also, tinker with some BIOS settings (one at a time, so you don't break anything and not know what!)

---

### Post by bobpur on 2006-04-10
[QUOTE=trent dillman]try passing 'noapic, nolapic' to grub on boot...also, tinker with some BIOS settings (one at a time, so you don't break anything and not know what!)[/QUOTE]

In the Bios I saw something called "APIC Mode"  When you click on it, it shows an enable/disable block. I changed it and it would go as far as "OK, booting the Kernel" and stop.
I removed the second harddrive, checked cables and shunt for the CD/ROM and floppy drive. Nothing so far has made a difference. It still boots as far as "Starting hotplug subsystem" and stalls there. Same results with Kubuntu. Can't get AMD 64 Ubuntu to install at all.

---

