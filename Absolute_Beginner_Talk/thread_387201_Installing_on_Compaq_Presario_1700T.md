---
title: "Installing on Compaq Presario 1700T"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by rzanoun on 2007-03-18
So.. when I try to start/install ubuntu from the 6.10 CD I've burned, I get the following message:

[COLOR="DarkOrange"][B][117179569.184000] Vendor PTLTD system has DSDT Revision 0x06040000 has a known ACPI Bios Problem
[117179569.184000] ACPI: Reason: Multiple Problems: This is a non-recoverable error[/B][/COLOR]

I think this sounds pretty serious, since the disc spins for a while before calling it quits.
I am running the memory tests just to make sure the machine is up to par. It currently has 64M or RAM, but I know that the minimal installtion requires only 32.

Initially I thought the Power-On password was tripping it up, but even when I disabled it, I still get the above error.

Any ideas?

BTW this machine is running Windows 98 (painful, I know) and its stats are:
Compaq Presario 1700t
Celeron 593.2 MHz
L1 Cache: 32K
L2 Cache 128K
Memory: 64M
Chipset: Intel i440BX

---

### Post by chuckyp on 2007-03-18
If you look at the bottom of the first screen that comes up when you boot the CD there is an F key to list the options like F8 or something.  Hit that and look for the option to disable ACPI  I believe its acpi=false.   You can enter this by pressing F6 and apending it to the end of the line.

---

### Post by rzanoun on 2007-03-19
Unfortunately, that didn't work. I clicked F6 and the boot options line appeared to which I appended 'acpi=false'.  I also tried the online help that mentioned to attempt 'noapic' and 'nolapic'.  But I think acpi is NOT apic, but thought it was close!

I am really at a loss.

In fact, when I boot from the CD, I get the splash screen with the following 5 options:
1. Start or install Ubuntu
2. Start ubuntu in safe graphics mode
3. Check CD for defects
4. Memory test
5. Boot from first hard disk

The only 2 things that truly work from the above list is #5, which boots my Windoes 98 and, the memory test; which, if left un-interrupted runs all night.  If I actually try checking the CD for defects, I get the same error when attempting #1.

Any help would be appreciated guys.:confused:

---

### Post by Cyklopz on 2007-05-12
The problem with presario 1700Ts is that ACPI is broken.  I have one also and can not get battery functions to work in "linux".  There are fixes for this but they are somewhat complicated and I have not tried them yet.  Still, I have not had trouble running versions of Ubuntu on the 1700t that I have:

PIII 800m
192megs ram
CDRW, DVDrom, Floppy
30gig hdd
Linksys 16bit 10base wireless

One alternative for systems with low memory is DSL (damn small linux).

If you want to try and fix the acpi just search for acpi and presario 1700t and you should find the fixes for it.  There is a project, acpi4linux, I think.

Cy

---

### Post by bdmurray on 2007-05-22
I believe the correct syntax of the acpi option to pass to the kernel is "acpi=off".  At least that is what I found in "Documentation/kernel-parameters.txt" in a kernel source tree.

---

