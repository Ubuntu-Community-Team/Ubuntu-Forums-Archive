---
title: "Why do I get some APIC error on bootup if I &quot;Enable mouse/keyboard&quot; in my MoBo bios?"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by inktri on 2008-01-04
My 64-bit Ubuntu 7.10 keeps on rebooting while trying to load on startup. Another strange fact to add is there's a 1 in 20-30 chance my computer will successfully login and that doesn't correspond to the flags I append to the end of the kernel boot command (as described below) -- it's completely random!. This problem exists for everything: trying to start Ubuntu via the Live-CD, via hard drive, via recovery mode. I also believe this is a 64-bit problem because my 32-bit Live-CD works perfectly

I've checked the threads on these forums and have tried what people have suggested with little success:
> 1. appending noapic nolapic nosplash to boot sequence
2. updating my BIOS
3. appending noapic nolapic
4. appending noapic
5. acpi=off
6. acpi=ht


My relevant computer specs:
> 64bit Ubuntu 7.10, Gigabyte P35-DS3L (with latest BIOS), Q6600, GeForce 8400GS, LSI 21320 SCSI hba, 2x Hitachi 15k300 Ultrastar hard drives.

During bootup I'm getting:
> Inquiring remote APIC #2...
... APIC #2 ID: failed
... APIC #2 VERSION: failed
... APIC #2 SPIV: failed
SMP alternatives: switching to SMP code
Booting processor 2/3 APIC 0x1
Not responding.

Inquiring remote APIC #3...
... APIC #3 ID: failed
... APIC #3 VERSION: failed
... APIC #3 SPIV: failed
SMP alternatives: switching to SMP code
Booting processor 3/2 APIC 0x1
Not responding.

Inquiring remote APIC #1...
... APIC #1 ID: failed
... APIC #1 VERSION: failed
... APIC #1 SPIV: failed
SMP alternatives: switching to SMP code
Booting processor 3/2 APIC 0x1
Not responding.

The only solution to the above problem is to disable USB mouse/keyboard during bootup in my during bootup (USB mouse/keyboard still works, it's just I can't use them before Ubuntu is loaded -- in the Live CD, etc.) in my motherboard bios.  So I guess one solution would be to rely on a PS2 keyboard for that stuff; however my USB keyboard is really nice and I'd only like to bring that back to college. 

Anyone know a remedy?

Thank you very much

---

### Post by Sef on 2008-01-04
[Duplicate post.]("http://ubuntuforums.org/showthread.php?t=658155") Locked.

---

