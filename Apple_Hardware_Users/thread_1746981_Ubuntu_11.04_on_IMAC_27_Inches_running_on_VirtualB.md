---
title: "Ubuntu 11.04 on IMAC 27 Inches running on VirtualBox"
date: 2011-05-02
forum: Apple Hardware Users
---

### Post by Hachaso on 2011-05-02
Hi!

I have an IMAC 27 inches with these specs:

2.8GHZ QUAD-CORE INTEL CORE I7
8GB 1066MHZ DDR3 SDRAM - 4X2GB
1TB SERIAL ATA DRIVE
ATI RADEON HD 4850 512MB
8X DOUBLE-LAYER SUPERDRIVE
APPLE MAGIC MOUSE-Z

I installed VirtualBox and created a virtual machine and installed Ubuntu 11.04, I checked the 3D acceleration box but encountered problems running Unity. I suppose that I have the necessary hardware to be able to run Unity on my Imac with VirtualBox.

I tried to install the new [I]fglrx drivers but still encountered problems.

Has anyone encountered the same problems?
Any solutions?

Thanks
[/I]

---

### Post by pauljwells on 2011-05-03
[http://maketecheasier.com/enable-3d-acceleration-in-virtualbox/2009/05/21]("http://maketecheasier.com/enable-3d-acceleration-in-virtualbox/2009/05/21")

The fglrx driver is NOT what you want! You need a driver for the virtualised hardware presented by virtualbox. Take a look at the link.

---

