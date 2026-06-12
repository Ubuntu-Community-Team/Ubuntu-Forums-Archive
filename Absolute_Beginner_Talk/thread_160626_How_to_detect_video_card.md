---
title: "How to detect video card"
date: 2006-04-15
forum: Absolute Beginner Talk
---

### Post by jsmidt on 2006-04-15
I just bought a new computer and the user manuel says it either came with an Intel Graphics Media accelerator 950 or ATI Mobility Radeon X1300.  

I have two questions:
1.) How do I know which one I have?
2.) I could I figure out what parameters I needed to reconfigure x?

this is lspci output:

0000:00:02.0 VGA compatible controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03) (prog-if 00 [VGA])
        Subsystem: Toshiba America Info Systems: Unknown device ff10
        Flags: bus master, fast devsel, latency 0, IRQ 177
        Memory at dc100000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at 1800 [size=8]
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        Memory at dc200000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: <available only to root>

0000:00:02.1 Display controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03)
        Subsystem: Toshiba America Info Systems: Unknown device ff10
        Flags: bus master, fast devsel, latency 0
        Memory at dc180000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <available only to root>

---

### Post by localzuk on 2006-04-15
According to your output, you have the Intel one (hence "Intel Corporation Mobile Integrated Graphics Controller" :) ).

---

### Post by jsmidt on 2006-04-15
I found out this is my stuff:

Display Size :  15.4"
Display Type : Widescreen XGA with TruBrite Technology
Graphics Chipset : Graphics Media Accelerator 950
Graphics Memory : 8MB-128MB dynamically allocated shared graphics memory 

But again, what parameters do I put in when I run dpkg-reconfigure xserver-xorg?  My lspci info is above.  Thanks

---

### Post by localzuk on 2006-04-15
Try using the i810 driver. It seems to be the one for the i915 chipset and there aren't any better ones for intel chips.

Take a look at [https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsToshiba](https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsToshiba) also.

---

