---
title: "Needing help discovering hardware"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by davo_ on 2007-04-13
First problem:

I cannot seem to change my screen resolution above 1024x780, or my screen refresh rate to anything better than 0hz.  (It's a widescreen monitor, Gateway MX 3228 laptop) I am unable to figure out what my video card is, I thought the command was 'lspci' but I'm only getting information regarding my networking hardware.

Any ideas to help me find out what my video card is, and where I can go to install the appropriate Linux drivers? 

(Also, I installed kubuntu desktop with apt-get and got an error while booting up, but I think I've fixed that problem...will post again here if not)

---

### Post by PetePete on 2007-04-13
try using the command

sudo lshw

once you know what it is, post here and tell us and we can direct you to appropiate drivers.

---

### Post by davo_ on 2007-04-13
It's a bit...long winded but here's the output

dave-laptop               
    description: Portable Computer
    product: MX3228
    vendor: Gateway
    version: 73.08
    serial: N6364 910 07170
    width: 32 bits
    capabilities: smbios-2.34 dmi-2.34
    configuration: boot=oem-specific chassis=portable uuid=4D616769-632D-4C43-0756-00032537B5A1
  *-core
       description: Motherboard
       vendor: Gateway
       physical id: 0
       version: Rev1.73.08
       serial: V641M8U0074J5C420X
     *-firmware
          description: BIOS
          vendor: Phoenix
          physical id: 0
          version: 73.08 (03/10/2006)
          size: 90KB
          capacity: 448KB
          capabilities: pci pcmcia pnp apm upgrade shadowing escd cdboot bootselect edd int13floppynec int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) M processor         1.50GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.13.8
          slot: Socket 478
          size: 1500MHz
          capacity: 3GHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe up
        *-cache
             description: L2 cache
             physical id: 5
             slot: L2 Cache
             size: 1MB
             capabilities: burst external write-through data
     *-memory
          description: System Memory
          physical id: 7
          slot: System board or motherboard
          size: 512MB
        *-bank
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: M1
             size: 512MB
             width: 64 bits
     *-pci:0
          description: Host bridge
          product: P4M800CE Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: c0000000
          bus info: pci@00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          resources: iomemory:c0000000-cfffffff
        *-pci
             description: PCI bridge
             product: VT8237 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: UniChrome Pro IGP
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@01:00.0
                version: 01
                size: 64MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                resources: iomemory:d0000000-d3ffffff iomemory:d4000000-d4ffffff irq:10
        *-pcmcia
             description: CardBus bridge
             product: Texas Instruments
             vendor: Texas Instruments
             physical id: c
             bus info: pci@00:0c.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus
             resources: iomemory:34000000-34000fff irq:177
        *-storage
             description: Mass storage controller
             product: Texas Instruments
             vendor: Texas Instruments
             physical id: c.2
             bus info: pci@00:0c.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: storage bus_master cap_list
             configuration: driver=tifm_7xx1
             resources: iomemory:34001000-34001fff irq:177
        *-system
             description: Generic system peripheral
             product: Texas Instruments
             vendor: Texas Instruments
             physical id: c.3
             bus info: pci@00:0c.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=sdhci
             resources: iomemory:34002200-340022ff irq:177
        *-network:0
             description: Wireless interface
             product: Realtek Semiconductor Co., Ltd.
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: e
             bus info: pci@00:0e.0
             logical name: wlan0
             version: 20
             serial: 00:c0:a8:b5:28:ed
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=rtl8180 multicast=yes wireless=802.11b/g
             resources: ioport:2800-28ff iomemory:34002000-340021ff irq:209
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@00:0f.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=VIA_IDE
             resources: ioport:1c80-1c8f irq:185
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: HTS541060G9AT00
                   vendor: Hitachi
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: MB3VA60A
                   serial: MPB3LAXGGHL4MM
                   size: 55GB
                   capacity: 55GB
                   capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
                   configuration: apm=off mode=udma5 smart=on
                 *-volume:0
                      description: Linux filesystem partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 54GB
                      capabilities: primary bootable
                 *-volume:1
                      description: Extended partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      capacity: 1286MB
                      capabilities: extended partitioned partitioned:extended
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   description: DVD writer
                   product: HL-DT-ST DVD-RW GWA-4082N
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: CG03
                   serial: M0063O22941
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy pm audio cd-r cd-rw dvd dvd-r
                   configuration: mode=udma2
                 *-disc
                      physical id: 0
                      logical name: /dev/hdc
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@00:10.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:1c00-1c1f irq:193
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@00:10.1
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:1c20-1c3f irq:193
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@00:10.2
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:1c40-1c5f irq:193
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Mouse
                   product: HP Mouse
                   vendor: Hewlett-Packard
                   physical id: 1
                   bus info: usb@3:1
                   version: 51.02
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
        *-usb:3
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@00:10.3
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:1c60-1c7f irq:193
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:4
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.4
             bus info: pci@00:10.4
             version: 86
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd
             resources: iomemory:d5200000-d52000ff irq:193
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.17-10-generic ehci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s
        *-isa UNCLAIMED
             description: ISA bridge
             product: VT8237 ISA bridge [KT600/K8T800/K8T890 South]
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
        *-multimedia
             description: Multimedia audio controller
             product: VT8233/A/8235/8237 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.5
             bus info: pci@00:11.5
             version: 60
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: driver=VIA 82xx Audio
             resources: ioport:1000-10ff irq:217
        *-communication
             description: Communication controller
             product: AC'97 Modem Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.6
             bus info: pci@00:11.6
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: driver=VIA 82xx Modem
             resources: ioport:1400-14ff irq:217
        *-network:1
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@00:12.0
             logical name: eth0
             version: 78
             serial: 00:03:25:37:b5:a1
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
             configuration: autonegociation=on broadcast=yes driver=via-rhine driverversion=1.2.0-2.6 duplex=full ip=172.16.4.83 link=yes multicast=yes port=MII speed=100MB/s
             resources: ioport:1800-18ff iomemory:d5200400-d52004ff irq:201
     *-pci:1
          description: Host bridge
          product: P4M800CE Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@00:00.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: P4M800CE Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 101
          bus info: pci@00:00.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: PT890 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 102
          bus info: pci@00:00.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: P4M800CE Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 103
          bus info: pci@00:00.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: P4M800CE Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 104
          bus info: pci@00:00.7
          version: 00
          width: 32 bits
          clock: 33MHz

---

### Post by louistan3 on 2007-04-13
*-display
description: VGA compatible controller
product: UniChrome Pro IGP
vendor: VIA Technologies, Inc.
physical id: 0
bus info: pci@01:00.0
version: 01
size: 64MB
width: 32 bits
clock: 66MHz
capabilities: vga bus_master cap_list
resources: iomemory:d0000000-d3ffffff iomemory:d4000000-d4ffffff irq:10

i believe this one is ur video card..  im sorry i cant help further as i am nt familiar with VIA video cards..

---

### Post by justleen on 2007-04-13
what you could try:
open a terminal by pressing ctrl-alt-2, and login
killl gdm ```
 sudo /etc/init.d/gdm stop 
```
create a backup of your xorg.conf ```
 sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup 
```
reconfigure X ```
sudo -dpkg-reconfigure xserver-xorg 
```
Most of the questions you can leave at default, if you dont know the answer.
When asked what module to use, look for VIA (in think its in there. correct me if im wrong, im @ work)

you will  be asked what resolutions you want to use, just thick the ones you want.

afterwards, restart X ```
  sudo /etc/init.d/gdm start 
```

---

### Post by davo_ on 2007-04-13
All went well until I got to 

sudo -dpkg-reconfigure xserver-xorg

and I was told -dpkg-reconfigure was an illegal option.

---

### Post by davo_ on 2007-04-13
Crisis averted, I took out the first hyphen before dpkg.

---

### Post by davo_ on 2007-04-14
Me again. I've tried configuring xserver, to no avail.  I only ended up screwing up the install, and having to start over again.  I suppose it would help better if I gave an idea of what I want to do:

I'd like to get my screen resolution at best, to 1280x768, and improve my screen refresh rate
Install Kubuntu
Make the full conversion from Gnome to Kubuntu

What would I have to do to get the appropriate drivers for my video card downloaded and installed?

---

### Post by cheesewhiz on 2007-04-20
Sorry to bump this, but I'm having the same problem, I have an XFX 7900GS and my monitor is a 22" widescreen Westinghouse if it helps.

---

### Post by zeeone on 2007-05-29
I have the exact same Gatway model as you and I was able to install the video driver following these steps:
[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

---

