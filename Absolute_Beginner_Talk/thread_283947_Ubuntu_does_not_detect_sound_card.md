---
title: "Ubuntu does not detect sound card"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by sdubois92 on 2006-10-24
I had to reinstall ubuntu yesterday and it didnt reconize my sound card. I dont know what type of card it is, it is the built in one for a IBM 300pl. Thats about all i know. please help.

---

### Post by IYY on 2006-10-24
Is it a desktop or a laptop? If it's a desktop, I'd suggest just buying a new card. They can be as cheap as $10.

---

### Post by taurus on 2006-10-24
Maybe these two commands will tell you what it is...

```

lspci
lshw

```

---

### Post by sdubois92 on 2006-10-25
lcpi gives me...

0000:00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:02.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:02.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:02.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:02.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:03.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 05)
0000:00:10.0 Communication controller: Agere Systems Venus Modem (V90, 56KFlex)
0000:01:01.0 VGA compatible controller: S3 Inc. Trio 64 3D (rev 01)

lshw gives me...

WARNING: you should run this program as super-user.
steven-desktop
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 256MB
     *-cpu
          product: Pentium III (Katmai)
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.7.2
          size: 500MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 32KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KB
     *-pci
          description: Host bridge
          product: 440BX/ZX/DX - 82443BX/ZX/DX Host bridge
          vendor: Intel Corporation
          physical id: ec000000
          bus info: pci@00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          resources: iomemory:ec000000-efffffff
        *-pci
             description: PCI bridge
             product: 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: Trio 64 3D
                vendor: S3 Inc.
                physical id: 1
                bus info: pci@01:01.0
                version: 01
                size: 64MB
                width: 32 bits
                clock: 33MHz
                capabilities: vga bus_master cap_list
                resources: iomemory:f4000000-f7ffffff irq:11
        *-isa UNCLAIMED
             description: ISA bridge
             product: 82371AB/EB/MB PIIX4 ISA
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
        *-ide
             description: IDE interface
             product: 82371AB/EB/MB PIIX4 IDE
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@00:02.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=PIIX_IDE
             resources: ioport:fff0-ffff
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   product: Maxtor 51024H2
                   vendor: Maxtor
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   capacity: 9765MB
              *-floppy
                   product: IOMEGA ZIP 100 ATAPI
                   physical id: 1
                   bus info: ide@0.1
                   logical name: /dev/hdb
                   capabilities: packet
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   product: SAMSUNG CD-ROM SC-148C
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   capabilities: packet
        *-usb
             description: USB Controller
             product: 82371AB/EB/MB PIIX4 USB
             vendor: Intel Corporation
             physical id: 2.2
             bus info: pci@00:02.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:ff00-ff1f irq:10
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-27-386 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: USB hub
                   product: TUSB2040/2070 Hub
                   vendor: Texas Instruments, Inc.
                   physical id: 2
                   bus info: usb@1:2
                   version: 1.10
                   capabilities: usb-1.10
                   configuration: driver=hub maxpower=100mA slots=4 speed=12.0MB/s
                 *-usb
                      description: Mouse
                      product: Apple Optical USB Mouse
                      vendor: Mitsumi Electric
                      physical id: 3
                      bus info: usb@1:2.3
                      version: 1.08
                      capabilities: usb-1.10
                      configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
        *-bridge UNCLAIMED
             description: Bridge
             product: 82371AB/EB/MB PIIX4 ACPI
             vendor: Intel Corporation
             physical id: 2.3
             bus info: pci@00:02.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bridge
             resources: irq:9
        *-network
             description: Ethernet interface
             product: 82557/8/9 [Ethernet Pro 100]
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@00:03.0
             logical name: eth0
             version: 05
             serial: 00:06:29:12:ab:fb
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=e100 ip=192.168.1.102 multicast=yes
             resources: iomemory:f3dff000-f3dfffff ioport:7c60-7c7f iomemory:f3f00000-f3ffffff irq:10
        *-communication
             description: Communication controller
             product: Venus Modem (V90, 56KFlex)
             vendor: Agere Systems
             physical id: 10
             bus info: pci@00:10.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=serial
             resources: iomemory:f3efff00-f3efffff ioport:7400-74ff ioport:7800-78ff ioport:7c58-7c5f irq:9

---

### Post by Kateikyoushi on 2006-10-25
Copy this to a terminal.

```
modprobe snd-cs4236;modprobe snd-pcm-oss;modprobe snd-mixer-oss;modprobe snd-seq-oss
```

If it works try

```
aplay -l
```

---

### Post by sdubois92 on 2006-10-25
doesnt work,

device_list:221: no soundcards found...

---

