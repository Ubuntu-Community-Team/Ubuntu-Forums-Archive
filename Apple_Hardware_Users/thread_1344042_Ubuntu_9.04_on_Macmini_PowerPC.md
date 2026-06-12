---
title: "Ubuntu 9.04 on Macmini PowerPC"
date: 2009-12-02
forum: Apple Hardware Users
---

### Post by Jubalgunn on 2009-12-02
Hi All,
I have recently installed Ubuntu 9.04 PowerPC on my Macmini.
Everything works except for the graphics.
When I run - gedit /etc/X11/xorg.conf
I get this-



ction "Device"
	Identifier	"Configured Video Device"
	BusID		"PCI:0:16:0"
	Option		"UseFBDev"		"true"

if I run glxinfo I get - it tells me rendering is enabled
GLX gears also runs.
How to enable the ATI open drivers/
Do I have to reconfigure xorg.conf with bespoke settings?
I have compiz settings manager installed but dont appear to be able to enable the 3D graphic drivers Radeon R280 9200.
Any help would be appreciated.:D

---

### Post by ajgreeny on 2009-12-02
Have you installed any other driver for your card?  I think that is the same card as I have, ATI 9200SE, but you can check with** lshw -C display** in terminal.  Here's my output from that:-
> lshw -C display
WARNING: you should run this program as super-user.
  *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: RV280 [Radeon 9200 PRO]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=32 mingnt=8
       resources: memory:d0000000-d7ffffff(prefetchable) ioport:c000(size=256) memory:e5000000-e500ffff memory:e4000000-e401ffff(prefetchable)
  *-display:1 UNCLAIMED
       description: Display controller
       product: RV280 [Radeon 9200 PRO] (Secondary)
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:02:00.1
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: cap_list
       configuration: latency=32 mingnt=8
       resources: memory:d8000000-dfffffff(prefetchable) memory:e5010000-e501ffff
I have the ati/radeon open source driver running, as it was at install without me adding or doing anything else, but in 9.10 I can not run compiz at higher res than 1024x768 unless I run at 16 bit colour.  In previous ubuntu versions the card ran compiz perfectly.  You may have the same problem, but I don't know if macs are different to PCs in this respect.

---

