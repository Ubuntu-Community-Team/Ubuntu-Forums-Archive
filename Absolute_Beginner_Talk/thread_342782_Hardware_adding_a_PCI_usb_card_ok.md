---
title: "Hardware: adding a PCI usb card ok?"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by keithpeter on 2007-01-20
Hello All

I have a recycled IBM Netvista 6790 which has a P4 processor and supports USB 1.1 from the motherboard. I'm running Xubuntu 6.06 fine and stable.

I'd like to use one of the PCI slots to add a Belkin Usb 2.0 card with two USB sockets so I can talk to the external hard drives more quickly.

Will Xubuntu recognise both USB controllers OK and allow them to work (USB DSL modem and sticks, cameras, MP3 player on USB 1.1 and the external hard drives on the PCI card at USB 2 speeds)

Thanks

---

### Post by keithpeter on 2007-01-21
It worked, and adds the following to the lshw. Not quite 40 times faster, but transferring 1.6 Gb of music files from my external drive to the computer hard drive now takes 80 seconds rather than 20 minutes.

```

           *-usb:2
                description: USB Controller
                product: USB 2.0
                vendor: NEC Corporation
                physical id: c.2
                bus info: pci@02:0c.2
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: ehci bus_master cap_list
                configuration: driver=ehci_hcd
                resources: iomemory:f2003000-f20030ff irq:201
              *-usbhost
                   product: EHCI Host Controller
                   vendor: Linux 2.6.15-27-686 ehci_hcd
                   physical id: 1
                   bus info: usb@5
                   logical name: usb5
                   version: 2.06
                   capabilities: usb-2.00
                   configuration: driver=hub maxpower=0mA slots=3 speed=480.0MB/s


```

---

