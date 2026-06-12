---
title: "128gb Limit / G4 Cube"
date: 2007-04-05
forum: Apple PPC Users
---

### Post by wanax on 2007-04-05
I have a G4 cube, where I was considering installing Ubuntu server once I upgrade the harddrive. I know that there is generally a 128gb limit on HD size on the internal bus, however for OS X, there is a kernel extension workaround ( [http://www.speedtools.com/ATA6.shtml](http://www.speedtools.com/ATA6.shtml) ). It also appears that at least in one case running BSD doesn't trigger the problem (eg. [http://osdir.com/ml/openbsd.ppc/2007-02/msg00002.html](http://osdir.com/ml/openbsd.ppc/2007-02/msg00002.html)
[http://macosx.com/forums/hardware-peripherals/291168-any-hard-drive-limit-imac-g3.html](http://macosx.com/forums/hardware-peripherals/291168-any-hard-drive-limit-imac-g3.html) )

This implies that there are software workarounds. I was wondering if Ubuntu is able to operate the full capacity of a larger than 128gb drive on a computer like the G4 Cube, or is it constrained by the hardware? I've searched the forums, but wasn't able to find anything definitive.

---

### Post by ZoiaGuyver on 2007-04-06
afaik the constraint is limited to the OF used in all the Mac G4's the workaround for OS X tbh is probably simple as that has direct access to the OF, where as Linux (Ubuntu or others) does not. 

I should imagine if you could somehow get it to dual boot with the patch in the system folder it would work as OF would report to the kernel the drive was larger than 128gb (this is just a guess though).

Tbh i have heard a few rumours of this but as yet havnt actually seen anything that works. Being OF is basically a Apple version of the bios i would suppose any changes directly made to it would affect the whole system but if the workaround is just OS based and not OF based it wouldnt work in anything but Mac OS.

Hope this helps a bit.

---

### Post by anders_gud on 2007-04-06
> **wanax said:**
> 
I was wondering if Ubuntu is able to operate the full capacity of a larger than 128gb drive on a computer like the G4 Cube, or is it constrained by the hardware? I've searched the forums, but wasn't able to find anything definitive.

I'd say try it...
I did something like this on a old PII - the bios could not see the drive, Debian did. All you had to do was to boot from another media (floppy in this case). Uptime over two years, no file corruption or other problems...
Good luck!

---

### Post by wanax on 2007-05-04
To answer my own question:

I've now tried installing Ubuntu 6.06 Server Edition on my G4 Cube with a 500gb internal hard drive. It fails to work with either a single large partition, or multiple ~120gb partitions. In the latter case, the first partition is readable and works fine (boots etc.), the rest aren't accessible.

---

### Post by DJ_Max on 2007-05-06
This is NOT a OpenFirmware issue, it's a IDE controller issue which was a problem untill Apple switched to a new controller on their computers. It doesn't matter how you partition it, it will not work. This is a hardware limitation.

The easiest solution is to buy a ATA-100/133 PCI card (a SATA PCI card should work as well.) As long as it has support for LBA-48 (Long Block Addressing) mode, most, if not all today support this.

You could also use another interface besides IDE (FireWire, USB, SCSI, etc.)

---

### Post by BoneKracker on 2007-05-07
You might want to actually check out the controller to see whether it can use 48-bit addressing.

My G4 500 (AGP) is not supposed to be able to use the larger drives either (according to Apple and everybody else with an opinion on the matter) -- but it can.  I recently put a 300 GB ultraATA drive into it, and I have tested it thoroughly.  I am able to use all of it.  

I think mine is a weird case though (my machine was made shortly before the subsequent model (G4 with "silver doors") was released.  That subsequent model is supposedly the oldest Mac that can use the >137GB drives.  (My machine also came with a wider AGP bus and more GPU RAM than it is supposed to have.)

In all likelihood, though, you will require an adapter.

---

