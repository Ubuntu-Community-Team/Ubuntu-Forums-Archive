---
title: "Applications menu &amp; drivers"
date: 2008-10-27
forum: Apple Hardware Users
---

### Post by ReaRea on 2008-10-27
I just got Xubuntu 6.06 on a iBook Clamshell M6411
Two questions
1) After a few times clicking the apps menu in the top left, it doesnt open any more. If I reinstall Xubuntu, it works then stops again. Is there any reason for it?

2) Trying to get the ethernet port working. Cant find the drivers for it. Any help appreciated

lshw -C network
```
WARNING: you should run this program as super-user.
  *-generic DISABLED
       description: Ethernet interface
       product: UniNorth GMAC (Sun GEM)
       vendor: Apple Computer Inc.
       physical id: f
       bus info: pci@20:0f.0
       logical name: eth0
       version: ff
       serial: 00:30:65:b3:ad:66
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master vga_palette cap_lis t ethernet physical
       configuration: broadcast=yes driver=gem mult icast=yes
       resources: iomemory:f5200000-f53fffff irq:41
```
ifconfig
```
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:172 (172.0 b)  TX bytes:172 (172.0 b)
```
 lspci
```
0000:00:0b.0 Host bridge: Apple Computer Inc. UniNort h AGP
0000:00:10.0 VGA compatible controller: ATI Technolog ies Inc Rage Mobility M3 AGP 2x (rev 02)
0001:10:0b.0 Host bridge: Apple Computer Inc. UniNort h PCI
0001:10:17.0 ff00: Apple Computer Inc. KeyLargo Mac I /O (rev 03)
0001:10:18.0 USB Controller: Apple Computer Inc. KeyL argo USB
0001:10:19.0 USB Controller: Apple Computer Inc. KeyL argo USB
0002:20:0b.0 Host bridge: Apple Computer Inc. UniNort h Internal PCI
0002:20:0e.0 FireWire (IEEE 1394): Apple Computer Inc . UniNorth FireWire (rev 01)
0002:20:0f.0 ffff: Apple Computer Inc. UniNorth GMAC (Sun GEM) (rev ff)
```

---

### Post by stream303 on 2008-10-28
Does
```
sudo ifup eth0
```

help?

I know that during a rushed install, I inadvertently let the system think that the firewire port was to be used for "ethernet-over-firewire" and that caused problems.  Not sure if you've done that here - hopefully bringing the interface up manually might help.

I think I found this by accident once by being able to bring up the interface on eth1 instead, but it seems like you've got it right.

---

### Post by ReaRea on 2008-10-29
I'm thinking the fact it says "DISABLED" may be the problem? Is there a way to enable this?

lshw -C network
```
  *-generic DISABLED
       description: Ethernet interface
       product: UniNorth GMAC (Sun GEM)
       vendor: Apple Computer Inc.
       physical id: f
       bus info: pci@20:0f.0
       logical name: eth0
       version: ff
       serial: 00:30:65:b3:ad:66
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master vga_palette cap_lis t ethernet physical
       configuration: broadcast=yes driver=gem mult icast=yes
       resources: iomemory:f5200000-f53fffff irq:41
```

---

