---
title: "Yaboot stuck after kernel update"
date: 2009-02-04
forum: Apple Hardware Users
---

### Post by abelthorne on 2009-02-04
Hello,
Ive tried to install Ubuntu PPC on a G5 iMac. As there was no LiveCD version for Intrepid, I installed Hardy and upgraded it to Intrepid.

While tidying packages in Synaptic, I saw that there was a kernel package that was noted as "now", meaning it was not from the current (Intrepid) repos.

Thinking it was an obsolete Hardy kernel, I installed linux-image-powerpc (headers were already installed) and were asked to reboot. I did not remove other kernel-related packages.

After I reboot, Yaboot crashes : after I select Linux and press enter at command line (boot options), I get a blank screen with the following :
```
done
found display   : /pci@0,f0000000/NVDA,Parent@10/NVDA,Display-B@1, opening ... done
copying of device tree ...
Building dt strings...
Building dt structure...
Device tree strings 0x02653000 -> 0x02654537
Device tree struct  0x02655000 -> 0x0265f000
Calling quiesce ...
returning from prom_init

Invalid memory access at   %SRR0: 00000000.01403984   %SRR1:  10000000.00083030

Apple PowerMac8,1 5.2.2f4 BootROM built on 11/09/04 at 11:06:15
Copyright 1994-2004 Apple Computer, Inc.
All Rights Reserved.

Welcome to Open Firmware, the system time and date is 20:12:47 02/04/2009

To continue booting, type "mac-boot" and press return.
To shut down, type "shut-down" and press return.

Release keys to continue!
```
And it is stuck. I can't type anything and don't have key pressed (I don't understand why it says to release keys at the end).

It seems all I can do is turn the Mac off.

Can this be fixed or do I have to reinstall Ubuntu ?

---

### Post by abelthorne on 2009-02-04
In fact I can boot from the "old" kernel. I didn't understand it was a separate one.

EDIT : problem solved

---

