---
title: "not (enable desktop effects) in  imac"
date: 2007-10-18
forum: Apple PPC Users
---

### Post by sunnyhanda on 2007-10-18
I tried to enable desktop effects but all i get white screen then nothing happens.....

iam using imac g3, 1 gig RAM, 20 gig hard drive.


following are the specs: 

imac@imac-apple:~$ lspci
0000:00:0b.0 Host bridge: Apple Computer Inc. UniNorth AGP
0000:00:10.0 Display controller: ATI Technologies Inc Rage 128 PR/PRO AGP 4x TMDS
0001:10:0b.0 Host bridge: Apple Computer Inc. UniNorth PCI
0001:10:17.0 Class ff00: Apple Computer Inc. KeyLargo Mac I/O (rev 03)
0001:10:18.0 USB Controller: Apple Computer Inc. KeyLargo USB
0001:10:19.0 USB Controller: Apple Computer Inc. KeyLargo USB
0002:20:0b.0 Host bridge: Apple Computer Inc. UniNorth Internal PCI
0002:20:0e.0 FireWire (IEEE 1394): Apple Computer Inc. UniNorth FireWire (rev 01)
0002:20:0f.0 Ethernet controller: Apple Computer Inc. UniNorth GMAC (Sun GEM) (rev 01)
imac@imac-apple:~$ sudo -imac
sudo: please use single character options
Password:
root@imac-apple:~# sudo modprobe -r fglrx
FATAL: Module fglrx not found.
root@imac-apple:~# sudo lshw -class display
  *-display               
       description: Display controller
       product: Rage 128 PR/PRO AGP 4x TMDS
       vendor: ATI Technologies Inc
       physical id: 10
       bus info: pci@00:10.0
       logical name: /dev/fb0
       version: 00
       size: 64MB
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list fb accelerated
       configuration: depth=32 driver=aty128fb frequency=75.03Hz latency=255 mingnt=8 mode=1024x768 visual=directcolor xres=1024 yres=768
       resources: iomemory:94000000-97ffffff ioport:400-4ff iomemory:90000000-90003fff irq:48

---

### Post by stmiller on 2007-10-19
There is no fglrx for PowerPC.

Type 
```

glxinfo

```
into a terminal and look for 

direct rendering: Yes

at the top. This is required before desktop effects can work.

Also, are you running as root? You can get a temp root shell by issuing:
```

sudo -s

```
There is no need to do the "sudo + command" if you are root or in a root shell. You only have to issue 'sudo + ___' if you are a no-root user to gain temporary access.

---

