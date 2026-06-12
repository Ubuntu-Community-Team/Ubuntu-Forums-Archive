---
title: "[SOLVED] Resolution Problems on install"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by Sabar on 2007-11-10
I am installing Feisty on a used Dell that I picked up recently. I seem to be having two problems with the install.

First      for some reason the Resolution is set at 640x480 with a refresh rate of 85 Hz and rotation of normal. I have no idea what is in this thing for a video card and to be honest I dont know how to find out I read some posts that had xorg.conf in them but that didnt do anything for me I am currently working on that computer with the live CD in it 


Second    I don't know why but when I try to log onto feisty on this used computer " using installed not the Live CD " for some reason the letters I type into the login screen are funny looking and small  and I am told I have the wrong user name and password. I think if I do a new install I can fix this but rechecking my Keyboard on the install but I thought I would ask if there is something else I should know about?  Oh yea everything looks ok when I type using the Live CD.

---

### Post by matthewcraig on 2007-11-10
Use the Screens and Graphics tool under System -> Administration to set your monitors and resolution.

---

### Post by carlinuxlearner on 2007-11-10
So let me make sure I've got this straight. You CAN'T login to your installed version, The Live disk seams to work fine? 
Well I would boot up the "recovery mode" kernel and execute this "dpkg-reconfigure xserver-xorg"
then restart your computer, and do as "matthewcraig" suggested.

C@RL

---

### Post by Sabar on 2007-11-10
alright after reading more posts I did this 

sudo lshw | less

and got this

ubuntu
    description: Mini Tower Computer
    product: OptiPlex GX260
    vendor: Dell Computer Corporation
    serial: HXKQV21
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: administrator_password=enabled boot=normal chassis=mini-tower power-on
_password=enabled uuid=44454C4C-5800-104B-8051-C8C04F563231
  *-core
       description: Motherboard
       product: 02X378
       vendor: Dell Computer Corp.
       physical id: 0
       serial: ..CN1374035701T0.
       slot: PCI1
     *-firmware
          description: BIOS
          vendor: Dell Computer Corporation
          physical id: 0
          version: A06 (04/28/2003)
          size: 64KB
          capacity: 448KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect edd int1
3floppytoshiba int5printscreen int9keyboard int14serial int17printer acpi usb agp ls120bo
ot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.40GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 15.2.7
          slot: Microprocessor
          size: 2400MHz
          capacity: 3060MHz
          width: 32 bits
          clock: 533MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr
 pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 8KB
             capacity: 8KB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 512KB
             capacity: 512KB
          capabilities: internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 512MB
          capacity: 1GB
        *-bank:0
             description: DIMM SDRAM Synchronous 266 MHz (3.8 ns)
             physical id: 0
             slot: DIMM_A
             size: 256MB
             width: 64 bits
             clock: 266MHz (3.8ns)
        *-bank:1
             description: DIMM SDRAM Synchronous 266 MHz (3.8 ns)
             physical id: 1
             slot: DIMM_B
             size: 256MB
             width: 64 bits
             clock: 266MHz (3.8ns)
     *-pci
          description: Host bridge
          product: 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: f0000000
:
      bus info: pci@00:00.0
          version: 01
          width: 32 bits
          clock: 33MHz
          resources: iomemory:f0000000-f7ffffff
        *-display
             description: VGA compatible controller
             product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@00:02.0
             version: 01
             size: 128MB
             width: 32 bits
             clock: 33MHz
             capabilities: vga bus_master cap_list
             configuration: driver=i810_smbus latency=0
             resources: iomemory:e8000000-efffffff iomemory:ff680000-ff6fffff irq:16
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 01
             width: 32 bits
:
          clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:ff80-ff9f irq:16
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-15-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Mouse
                   product: Basic Optical Mouse
                   vendor: Microsoft
                   physical id: 2
                   bus info: usb@1:2
                   version: 0.00
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
        *-usb:1
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
:
         physical id: 1d.1
             bus info: pci@00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:ff60-ff7f irq:17
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-15-generic uhci_hcd
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
             version: 01
             width: 32 bits
             clock: 33MHz
         capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:ff40-ff5f irq:18
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-15-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:3
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: iomemory:ffa00800-ffa00bff irq:19
           *-usbhost
                product: EHCI Host Controller
:
           product: EHCI Host Controller
                vendor: Linux 2.6.20-15-generic ehci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=6 speed=480.0MB/s
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-network
                description: Ethernet interface
                product: 82540EM Gigabit Ethernet Controller
                vendor: Intel Corporation
                physical id: c
                bus info: pci@01:0c.0
                logical name: eth0
                version: 02
              serial: 00:0b:db:3d:23:f3
                size: 100MB/s
                capacity: 1GB/s
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt
 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e1000 driverversio
n=7.3.15-k2-NAPI duplex=full firmware=N/A ip=192.168.0.3 latency=64 link=yes mingnt=255 m
ulticast=yes port=twisted pair speed=100MB/s
                resources: iomemory:ff8e0000-ff8fffff ioport:ecc0-ecff irq:18
        *-isa
             description: ISA bridge
             product: 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 01
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
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated scsi-host
             configuration: driver=ata_piix latency=0
             resources: ioport:1f0-1f7 ioport:3f4-3f3 ioport:170-177 ioport:374-373 iopor
t:ffa0-ffaf iomemory:20000000-200003ff irq:18
           *-disk:0
                description: SCSI Disk
                product: IC35L080AVVA07-0
                vendor: ATA
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: VA4O
                serial: VNC404A4DY5ELF
                size: 74GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: Linux filesystem partition
                   physical id: 1
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
                   size: 1466MB
                   capacity: 1466MB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1466MB
                      capabilities: nofs
           *-disk:1
                description: SCSI Disk
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/sdb
                configuration: ansiversion=5
           *-cdrom
             description: DVD reader
                product: CDRW/DVD SM-348B
                vendor: SAMSUNG
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: T502
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
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:dc80-dc9f irq:11
    *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@00:1f.5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: ioport:d800-d8ff ioport:dc40-dc7f iomemory:ffa00400-ffa005ff iome
mory:ffa00000-ffa000ff irq:20



ok that was a lot of copy and paste I dont really know what everything is here does anybody see what can be the problem?

thanks if there is other info you can use please let me know where to get it.
Sabar

---

### Post by carlinuxlearner on 2007-11-10
Please try this:
1. Boot up the "recovery mode" kernel 
2. Execute this "dpkg-reconfigure xserver-xorg"
3. answer questions accordingly.
4. Restart your computer.
5. You keyboard should now be configured correctly, so try logging in.
6. Do as "matthewcraig" suggested.

C@RL

---

### Post by Sabar on 2007-11-10
How do I boot up the recovery mode kernel in feisty?

I cant find screen and graphics tool under System > Administration

I was thinking my resolution problem was stemming from a Graphics card issue. that's why I posted my last post with everything on it.

Thanks for helping guys.
Sabar

---

### Post by matthewcraig on 2007-11-10
Oh, you're using Feisty.

Have you considered doing a fresh install of the new Gutsy version?

---

### Post by Sabar on 2007-11-10
you know I think I have a cd for that maybe I will just give that a try.

---

### Post by matthewcraig on 2007-11-10
Once you get up and running... take a look at your state's Ubuntu Local Community Team.  You'll find them very helpful, so I recommend joining the organization.

---

### Post by carlinuxlearner on 2007-11-10
to boot up into "recovery mode" select the recovery mode kernel on the grub boot menu (you might have to click esc to see the grub boot menu).

C@RL

---

### Post by Sabar on 2007-11-13
Thanks everyone. Right at the moment it is looking like my problem is with my on-board video card.
Unfortunately I don't have a spare card to though on it at the moment to check my theory, But hopefully I will have one soon.   

I wasn't even aware of the fact that each state has its own Ubuntu Club. I cant wait to look into this a little further. Thanks again everyone.

---

### Post by Sabar on 2007-11-18
Thought I would finish this post out. Problem fixed. Thank you matthewcraig for suggesting I install Gutsy. That was all it took. 

Gutsy went right in video and audio ( both on-board ) worked out just fine. Now I am off to see what differences there are in feisty and Gutsy. 

Thanks to every one who responded.

Sabar

---

