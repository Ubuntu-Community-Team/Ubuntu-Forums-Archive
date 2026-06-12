---
title: "AtI radeon 9200 AGP showing as PCI???"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by newbiebob on 2007-06-11
Hi First Post here so sorry if in wrong place. 

I have a Ati radeon 9200 pro AGP video card, but unbuntu shows it has a PCI card. I have no PCI video card. The device manager shows it as a PCI video even after I edit it to show it as a agp card. From my edit of xorg.conf file
Section "Device"
	Identifier	"ATI Technologies Inc RV280 [Radeon 9200 PRO]"
	Driver		"ati"
	BusID		"AGP:1:0:0"
but still device manager shows it as PCI.
 

Tried various methods listed here to install an ATI video card driver every single time I end up with a dos like screen, the xserver gnome would not start at all. Cause of this needed to reinstall Ubuntu 5 times. Also can not unistall the new driver after install must reinstall ubuntu to get rid of them.

Please keep any advice very very simple I am new to linux.

---

### Post by lazyart on 2007-06-11
AGP cards always show up in xorg.conf and PCI:1:0:0.  That is how it identifies AGP.

This falls under "If it ain't broke, don't fix it" motto.  Install the system, let it be.  Once in the GUI, to go System>Administration>Restricted Drivers and enable the driver for ATI and be done with it.

---

### Post by saxin on 2007-06-11
You know how I can enable restricted ATI-driver with ATI Radeon 9200 agp-card? I tried going to the "Restricted Drivers", but got a message that said I did'nt need to. Is it impossible to use the restricted driver so I can play games like World of Warcraft? The opensource driver cant do the job :(

---

