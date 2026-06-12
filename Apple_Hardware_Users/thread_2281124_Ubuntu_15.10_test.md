---
title: "Ubuntu 15.10 test"
date: 2015-06-04
forum: Apple Hardware Users
---

### Post by rican-linux on 2015-06-04
I decided to get the daily 51.10 lubuntu iso from QA tracker to see where it is. I am seeing the same issues with 15.04, Xorg bad colors, ubiquity crashing, firefox buggy.. at least I let them know people are testing for powerpc

---

### Post by luigiburdo on 2015-06-04
> **rican-linux said:**
> I decided to get the daily 51.10 lubuntu iso from QA tracker to see where it is. I am seeing the same issues with 15.04, Xorg bad colors, ubiquity crashing, firefox buggy.. at least I let them know people are testing for powerpc

If they will continue use Qemu instead the real hardware ... this issues will be 4ever

---

### Post by rican-linux on 2015-06-04
They do not use real hardware?!?!?

---

### Post by luigiburdo on 2015-06-04
Simply supposition... 
On Qemu cpu = g4 totally emulated everything working right .
On MacMini G4 wrong colors 
On qemu kvm cpu g4 wrong colors 
On Qemu Kvm ppc 64 Xorg crash ...

they use qemu instead real hardware...

---

### Post by rican-linux on 2015-06-04
I just joined the lubuntu-qa mailing list and mentioned that I would love help in powerpc testing with my iBook and PowerMac. So we will see how it goes!

---

### Post by Spectre660 on 2015-06-04
I monitor these pages for any changes to the Mesa and Xorg-server packages before I  bother to test 15.10 again .
[https://launchpad.net/ubuntu/+source/mesa](https://launchpad.net/ubuntu/+source/mesa)
[https://launchpad.net/ubuntu/+source/xorg-server](https://launchpad.net/ubuntu/+source/xorg-server)

---

### Post by este.el.paz on 2015-06-04
> **rican-linux said:**
> I just joined the lubuntu-qa mailing list and mentioned that I would love help in powerpc testing with my iBook and PowerMac. So we will see how it goes!

love [to] help??  I think I saw your post there . . . ??  "wxl" is the lead PPC guy . . . try to get in touch with him . . . .

e..

---

### Post by rican-linux on 2015-06-04
e.e.p. thanks for the suggestion

---

### Post by rican-linux on 2015-06-05
Some interesting things.. So without an xorg.conf file I get these errors 

```
[   174.877] (WW) Warning, couldn't open module fglrx
[   174.877] (II) UnloadModule: "fglrx"
[   174.877] (II) Unloading fglrx
[   174.877] (EE) Failed to load module "fglrx" (module does not exist, 0)
[   175.702] (WW) Warning, couldn't open module fglrx
[   175.702] (II) UnloadModule: "fglrx"
[   175.702] (II) Unloading fglrx
[   175.702] (EE) Failed to load module "fglrx" (module does not exist, 0)
[   175.733] (WW) Falling back to old probe method for modesetting
[   175.734] (WW) Falling back to old probe method for fbdev
```

When I add my xorg.conf file, these errors go away, however I am still gett the bad colors and graphics...

---

### Post by luigiburdo on 2015-06-05
i cant add xorg.conf ... if i did it i have black screen ... without woking (in case of 14.x) ... in case of 15.x ... black screen or xorg crash

---

### Post by rican-linux on 2015-06-05
Luigi, this was on your G5? Have you tried any of **[these]("http://mac.linux.be/content/xorgconf-g5-ppc-tower")**?

---

### Post by luigiburdo on 2015-06-06
that was for old g5 agp it was much more compatible with linux compared the quad.
in any way i will check it and report

---

### Post by rican-linux on 2015-06-06
you it could be b/c of the radeonhd card?

---

### Post by abtabt on 2015-09-29
up and running 15.10 beta 2  iGlob

Bus info          Device             Class      Description
===========================================================
                                     system     iMac LCD 15"
                                     bus        Motherboard
                  /proc/device-tree  memory     
                                     memory     2EiB System memory
                                     memory     2EiB SDRAM
                                     memory     SDRAM
cpu@0                                processor  7450, altivec supported
                                     memory     32KiB L1 Cache
                                     memory     256KiB L2 Cache (unified)
pci@0000:00:0b.0                     bridge     UniNorth/Pangea AGP
pci@0000:00:10.0                     display    NV11 [GeForce2 MX/MX 400]
pci@0001:10:0b.0                     bridge     UniNorth/Pangea PCI
pci@0001:10:17.0                     generic    KeyLargo/Pangea Mac I/O
pci@0001:10:18.0                     bus        KeyLargo/Pangea USB
pci@0001:10:19.0                     bus        KeyLargo/Pangea USB
pci@0002:20:0b.0                     bridge     UniNorth/Pangea Internal PCI
pci@0002:20:0e.0                     bus        UniNorth/Pangea FireWire
pci@0002:20:0f.0  enP2p32s15f0       network    UniNorth/Pangea GMAC (Sun GEM)
                  scsi0              storage    
scsi@0:0.1.0      /dev/cdrom         disk       DVD-RW  DVR-104

i use nvidiafb driver only unhash blacklist , and add sound driver ,and a xorg.conf , nomodeset and video=offb:off (yaboot)
i disable compositing and enable use less resources (MATE TWEAKS)
works good

---

### Post by rican-linux on 2015-09-29
Awesome!

---

### Post by luigiburdo on 2015-09-29
> **rican-linux said:**
> you it could be b/c of the radeonhd card?

what do you mean with b/c ? ;-)

---

### Post by xeno74 on 2015-09-30
> **abtabt said:**
> up and running 15.10 beta 2  iGlob

Bus info          Device             Class      Description
===========================================================
                                     system     iMac LCD 15"
                                     bus        Motherboard
                  /proc/device-tree  memory     
                                     memory     2EiB System memory
                                     memory     2EiB SDRAM
                                     memory     SDRAM
cpu@0                                processor  7450, altivec supported
                                     memory     32KiB L1 Cache
                                     memory     256KiB L2 Cache (unified)
pci@0000:00:0b.0                     bridge     UniNorth/Pangea AGP
pci@0000:00:10.0                     display    NV11 [GeForce2 MX/MX 400]
pci@0001:10:0b.0                     bridge     UniNorth/Pangea PCI
pci@0001:10:17.0                     generic    KeyLargo/Pangea Mac I/O
pci@0001:10:18.0                     bus        KeyLargo/Pangea USB
pci@0001:10:19.0                     bus        KeyLargo/Pangea USB
pci@0002:20:0b.0                     bridge     UniNorth/Pangea Internal PCI
pci@0002:20:0e.0                     bus        UniNorth/Pangea FireWire
pci@0002:20:0f.0  enP2p32s15f0       network    UniNorth/Pangea GMAC (Sun GEM)
                  scsi0              storage    
scsi@0:0.1.0      /dev/cdrom         disk       DVD-RW  DVR-104

i use nvidiafb driver only unhash blacklist , and add sound driver ,and a xorg.conf , nomodeset and video=offb:off (yaboot)
i disable compositing and enable use less resources (MATE TWEAKS)
works good

Awesome!

---

