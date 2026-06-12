---
title: "[SOLVED] New to Linux: Finding drivers for HW upgrades"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by m9ke on 2007-08-12
Edit:  USB upgrade successful; marking solved, will deal with remaining upgrades in separate threads.

New to Linux but with Fiesty up and running, I am going to do some upgrading on my old computer soon, and would like to hear some thoughts on drivers.

The upgrades are:
- ASUS N6200 GeForce 6200 128MB 64-bit DDR AGP 4X/8X video card (Nvidia chipset)
- Rosewill USB 2.0 adapter card (PCI)
- Western Digital Caviar SE16 WD5000AAKB 500GB IDE Ultra ATA100 Hard Drive
- NEC MultiSynch LCD 1700v LCD display

I have installed Fiesty on this computer and gotten it working with email, IM and of course ethernet.

I have enabled all repositories including restricted.

Is there a terminal or Synaptic procedure a person who is looking for drivers for devices like those I listed above?  When multiple options exist, is it sufficient to search the forums to see what experiences others have had with individual drivers?

Or is the installer smart enough to allow me to dump the existing Fiesty install, put in all the hardware and reinstall finding the drivers for me?

TIA!!

---

### Post by jpeddicord on 2007-08-12
The only thing I foresee some potential trouble with would be the NVIDIA card. Everything else should be recognized fine.

For the NVIDIA card, when you insert it and boot, a little icon called the Restricted Drivers Manager will appear in the notification area. Simply use that to install the driver if needed.

Jacob

---

### Post by m9ke on 2007-08-12
Thanks Jacob.  First card I will install is the USB 2.0.  I will post back here - maybe someone else can use the info as I figure it out.

Cheers - m9ke

---

### Post by m9ke on 2007-08-13
USB card installed.  I did not install any drivers, just installed the card and tried to boot the computer.  It booted normally. 
 
The  info on the hw is that there were two USB 1.x physical ports from the mobo  (SIS chipset) before the upgrade.  When I installed the PCI USB adapter I got 5 additional physical ports (NEC chipset):  4 on the back of the computer plus one on the card itself inside the case.  The upgrade card I installed is a Rosewill RC-101 USB 2.0 5-port PCI adapter.

lshw revealed the following wrt USB:

*-usb:0
            description: USB Controller
             product: USB 1.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1.2
             bus info: pci@00:01.2
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80
             resources: iomemory:dc101000-dc101fff irq:11
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.20-16-generic ohci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=3
speed=12.0MB/s

        *-usb:1
             description: USB Controller
             product: USB 1.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1.3
             bus info: pci@00:01.3
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80
             resources: iomemory:dc102000-dc102fff irq:11
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.20-16-generic ohci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=3
speed=12.0MB/s

        *-usb:2
             description: USB Controller
             product: USB
             vendor: NEC Corporation
             physical id: 9
             bus info: pci@00:09.0
             version: 43
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=32 maxlatency=42
mingnt=1
             resources: iomemory:dc103000-dc103fff irq:5
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.20-16-generic ohci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=3
speed=12.0MB/s

        *-usb:3
             description: USB Controller
             product: USB
             vendor: NEC Corporation
             physical id: 9.1
             bus info: pci@00:09.1
             version: 43
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=32 maxlatency=42
mingnt=1
             resources: iomemory:dc104000-dc104fff irq:3
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.20-16-generic ohci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2
speed=12.0MB/s

        *-usb:4
             description: USB Controller
             product: USB 2.0
             vendor: NEC Corporation
             physical id: 9.2
             bus info: pci@00:09.2
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32 maxlatency=34
mingnt=16
             resources: iomemory:dc105000-dc1050ff irq:11
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.20-16-generic ehci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=5
speed=480.0MB/s
     
Could I get some help in understanding the above, and particularly in ascertaining if all the 5 ports on the upgrade card are configured to run at USB 2.0 speed ie around 480 Mb/sec?

---

