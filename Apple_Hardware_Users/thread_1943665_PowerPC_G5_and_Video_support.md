---
title: "PowerPC G5 and Video support"
date: 2012-03-19
forum: Apple Hardware Users
---

### Post by jamesisin on 2012-03-19
Hello,

I'm building an old G5 with Ubuntu 10.04 and I'm not able to get the extras working with the video card.

Can I get compositing to work?

How?

What do you need to know to help me?

Thanks.

---

### Post by jamesisin on 2012-03-26
Does anyone actually use this part of the forums?

---

### Post by svtguy88 on 2012-03-26
We need more specs to even begin helping.  What video card?  What video driver?  With the release of 12.04 looming, why are you using 10.04?

---

### Post by jamesisin on 2012-03-26
If you will tell me what to run to get information about the video card I can post the output here.  It is the card which came with the machine.

(I am using 10.04 because 12.04 isn't yet released.)

---

### Post by svtguy88 on 2012-03-27
See your other thread...

---

### Post by jamesisin on 2012-04-21
Here are the requested outputs...

```
$ lspci
0000:f0:0b.0 Host bridge: Apple Computer Inc. U3 AGP
0000:f0:10.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200 Ultra] (rev a1)
0001:00:00.0 Host bridge: Apple Computer Inc. CPC945 HT Bridge
0001:00:01.0 PCI bridge: Apple Computer Inc. K2 HT-PCI Bridge
0001:00:02.0 PCI bridge: Apple Computer Inc. K2 HT-PCI Bridge
0001:00:03.0 PCI bridge: Apple Computer Inc. K2 HT-PCI Bridge
0001:00:04.0 PCI bridge: Apple Computer Inc. K2 HT-PCI Bridge
0001:00:05.0 PCI bridge: Apple Computer Inc. K2 HT-PCI Bridge
0001:01:07.0 Class ff00: Apple Computer Inc. K2 KeyLargo Mac/IO (rev 60)
0001:01:08.0 USB Controller: Apple Computer Inc. K2 KeyLargo USB
0001:01:09.0 USB Controller: Apple Computer Inc. K2 KeyLargo USB
0001:02:0d.0 Class ff00: Apple Computer Inc. K2 ATA/100
0001:02:0e.0 FireWire (IEEE 1394): Apple Computer Inc. K2 FireWire
0001:03:0f.0 Ethernet controller: Apple Computer Inc. K2 GMAC (Sun GEM)
0001:04:0c.0 IDE interface: Broadcom K2 SATA
0001:05:0b.0 USB Controller: NEC Corporation USB (rev 43)
0001:05:0b.1 USB Controller: NEC Corporation USB (rev 43)
0001:05:0b.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
```

```
$ glxinfo | grep OpenGL
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 2.1 Mesa 7.7.1
OpenGL shading language version string: 1.20
OpenGL extensions:
```

(Yes, there was nothing after the colon in that last line.)

---

### Post by svtguy88 on 2012-04-22
Hmm...you are definitely stuck in software rasterizer mode, which is no good.  I had that issue for a long time with the Geforce 6200 in my Powermac G4.

You graphics card (FX 5200 Ultra) is based on the same core, the nv34, as the card in the machine I'm using right now.  Granted, this isn't a PowerPC box, but that shouldn't matter.

Fire up synaptic, or software center or whatever your favorite package manager happens to be.  What version of nouveau is installed?

**edit**
I just read your threads again, as I had sort of forgotten what your issues were.  I would seriously just download 12.04 and install it.  I was stuck in software rasterizer mode on my G4 until this version was released.  I had spend HOURS trying to manually compile nouveau and get 3D support working, as if I recall correctly, 10.04 uses an old version of nouveau and it's dependencies.

Go for 12.04.

---

