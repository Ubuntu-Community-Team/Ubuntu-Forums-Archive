---
title: "Wireless USB Stick not showing up in network settings"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by ThornInc on 2006-12-12
Alright.  I've gotten my drivers set up for my Ashton Digital WRUB-2011i using ndiswrapper. 

I've blacklisted the prism2_usb module (even though I'm not really sure if I was supposed to do that.)

Now when I type 'lshw' in terminal my device shows up as *-usb UNCLAIMED like  so:

        *-usb
             description: USB Controller
             product: 82371AB/EB/MB PIIX4 USB
             vendor: Intel Corporation
             physical id: 7.2
             bus info: pci@00:07.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:1000-101f irq:5
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-27-686 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2            speed=12.0MB/s
             ** *-usb UNCLAIMED**
                   description: Generic USB device
                   product: Ashton Digital WRUB-2011i
                   vendor: AirVast Taiwan
                   physical id: 2
                   bus info: usb@1:2
                   version: 1.32
                   capabilities: usb-1.10
                   configuration: maxpower=500mA speed=12.0MB/s

Is this the reason my USB stick isn't showing up in Network Settings, and does anyone know how to fix this?

Thanks in advance!

---

