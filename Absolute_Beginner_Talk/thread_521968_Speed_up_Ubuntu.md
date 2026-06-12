---
title: "Speed up Ubuntu"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by Vuto on 2007-08-10
Is there anyway I can make my computer (ubuntu) run faster, I noticed with windows you could go to task manager and end all unnesessary tasks. 

But is there any way I could make my ubuntu computer run faster?

Thnx

~~~Vuto~~~

---

### Post by crispy_420 on 2007-08-10
Switch to "lighter" desktop for starters.

Custom kernel.

---

### Post by Vuto on 2007-08-10
lighter desktop?

and whats custom kernel

I am new to ubuntu

---

### Post by ramjet_1953 on 2007-08-10
What are your hardware specifications?

1. CPU type and speed?

2. How much RAM do you have?

3. What is your video card / chipset and how much RAM?

Regards,
Roger :cool:

---

### Post by Vuto on 2007-08-10
once again i am new to ubuntu how do I check those things

---

### Post by amazingtaters on 2007-08-10
type *sudo lshw* into terminal and post your specs. This gives you just about everything, so you will have to read through it and just give us what's important. No one needs to know your mobo manufacturer for instance.

---

### Post by SOULRiDER on 2007-08-10
> **amazingtaters said:**
> type *sudo lshw* into terminal and post your specs. This gives you just about everything, so you will have to read through it and just give us what's important. No one needs to know your mobo manufacturer for instance.

I believe you don't need sudo for that.

Vuto, a custom kernel is basically compiling Linux yourself, something i advice you not to try.

---

### Post by amazingtaters on 2007-08-10
hmm, well I've always sudo'd it, so I can't say I know if you need to sudo it or not. I just know that I do.

---

### Post by Tyke91 on 2007-08-10
lol... 

ways to make ubuntu faster


switch to the xfce desktop manager (it is lighter than gnome or kde... also known as xubuntu)

you can do this (i think, i've never tried it before) by going into a shell (console command) and typing 

```
 sudo apt-get install xubuntu-desktop 
```

then when you login, you can choose xcfe instead of gnome.



the task manager is called the system monitor, and you can get that by going into System>administration>system monitor


you can also define custom hotkeys to make ctrl+alt+del bring up the system monitor if you want to.


hope that helps :guitar:

---

### Post by Vuto on 2007-08-11
> **amazingtaters said:**
> type *sudo lshw* into terminal and post your specs. This gives you just about everything, so you will have to read through it and just give us what's important. No one needs to know your mobo manufacturer for instance.

k I did that heres what I got
> stan-desktop              
    description: Desktop Computer
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=desktop
  *-core
       description: Motherboard
       product: 8I848E
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
       version: 1.x
       slot: PRIMARY IDE
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: F3 (07/31/2003)
          size: 128KB
          capacity: 192KB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot
     *-cpu:0
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.40GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.9
          slot: Socket 478
          size: 2400MHz
          capacity: 3600MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 8KB
             capacity: 20KB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: b
             slot: External Cache
             size: 512KB
             capacity: 512KB
             capabilities: synchronous external write-back
     *-cpu:1 DISABLED
          description: CPU
          product: ( )
          vendor: Unknown
          physical id: 5
          bus info: cpu@1
          version: 15.2.9
          slot: Socket 478
          size: 2400MHz
          capacity: 3600MHz
          clock: 133MHz
          capabilities: ht
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 8KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KB
     *-memory
          description: System Memory
          physical id: 1d
          slot: System board or motherboard
          size: 512MB
          capacity: 3GB
        *-bank:0
             description: DIMM 333 MHz (3.0 ns)
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 512MB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:1
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
        *-bank:2
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 2
             serial: None
             slot: A2
     *-pci
          description: Host bridge
          product: 82865G/PE/P DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: e8000000
          bus info: pci@00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          resources: iomemory:e8000000-efffffff
        *-pci:0
             description: PCI bridge
             product: 82865G/PE/P PCI to AGP Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: NV34 [GeForce FX 5200]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@01:00.0
                version: a1
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5
                resources: iomemory:f8000000-f8ffffff iomemory:f0000000-f7ffffff irq:17
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:d800-d81f irq:17
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:d000-d01f irq:18
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:d400-d41f irq:19
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Mouse
                   product: Microsoft 3-Button Mouse with IntelliEye(TM)
                   vendor: Microsoft
                   physical id: 2
                   bus info: usb@3:2
                   version: 3.00
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
        *-usb:3
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: iomemory:fa100000-fa1003ff irq:20
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.20-16-generic ehci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=6 speed=480.0MB/s
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: 82
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-communication
                description: Modem
                product: HSP MicroModem 56
                vendor: PCTel Inc
                physical id: 2
                bus info: pci@02:02.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: hayes_16750 cap_list
                configuration: driver=serial latency=0
                resources: ioport:c000-c03f irq:16
           *-network
                description: Ethernet interface
                product: 82562EZ 10/100 Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@02:08.0
                logical name: eth0
                version: 82
                serial: 00:0d:61:2d:14:b7
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI duplex=full firmware=N/A ip=192.168.15.101 latency=32 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
                resources: iomemory:fa000000-fa000fff ioport:c400-c43f irq:21
        *-isa
             description: ISA bridge
             product: 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801DB (ICH4) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated scsi-host
             configuration: driver=ata_piix latency=0
             resources: ioport:1f0-1f7 ioport:3f4-3f3 ioport:170-177 ioport:374-373 ioport:f000-f00f iomemory:30000000-300003ff irq:19
           *-disk
                description: SCSI Disk
                product: ST380011A
                vendor: ATA
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 3.06
                serial: 3JV4EAYS
                size: 74GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: Linux filesystem partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 73GB
                   capabilities: primary bootable
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 1474MB
                   capacity: 1474MB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1474MB
                      capabilities: nofs
           *-cdrom
                description: DVD reader
                product: RW/DVD GCC-4480B
                vendor: HL-DT-ST
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.02
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5
              *-disc
                   physical id: 0
                   logical name: /dev/cdrom
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:1400-141f irq:12
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: ioport:e000-e0ff ioport:e400-e43f iomemory:fa101000-fa1011ff iomemory:fa102000-fa1020ff irq:22


---

### Post by Bofur on 2007-08-11
Your hardware seems like it would handle Ubuntu just fine. Ubuntu runs pretty fast for most people. What are you noticing that is slow about it? All I can recommend for you is to switch to Xubuntu which is a lighter and somewhat faster OS (its made for low end computers) and to remove unneeded files with Add/Remove Programs to free up Hard Drive space.

---

### Post by MenZa on 2007-08-11
Have you installed the correct graphics drivers for your system? If not, try using [Envy](http://www.albertomilone.com/nvidia_scripts1.html). You can install it by running:

```

wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu6_all.deb
sudo dpkg -i envy_0.9.7-0ubuntu6_all.deb

```

Then follow the instructions on the page.

---

