---
title: "Network Card Confusion"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by ofb on 2007-10-02
I've done a lot of reading the last few days. Things are getting less clear rather than more clear, so I need some help.

  *-network:1 DISABLED
       description: Ethernet interface
       product: 82557/8/9 [Ethernet Pro 100]

also,

o@bluefish:~$ sudo ifdown eth1
ifdown: interface eth1 not configured
o@bluefish:~$ sudo ifup eth1
SIOCSIFFLAGS: Resource temporarily unavailable
SIOCSIFFLAGS: Resource temporarily unavailable
SIOCSIFFLAGS: Resource temporarily unavailable
Failed to bring up eth1.

What's clear from reading is Linux doesn't like that card. Windows is fine with it.

Probably the simplest start is here
[http://linux.web.cern.ch/linux/scientific/hardware/eepro100.shtml](http://linux.web.cern.ch/linux/scientific/hardware/eepro100.shtml)

That looks good, but Ubuntu 7.04 doesn't have /etc/modules.conf, so over to /etc/modprobe.d where I can't find any reference to "alias eth1 e100". A full search reveals no "alias eth0" or "alias eth1" in any plain text file on my system.

The only reference to e100 is in /etc/modprobe.d/blacklist

# replaced by e100
blacklist eepro100

... which tells me the old fix probably isn't the thing to do anymore.

The last useful item I can establish is I don't get the very common "e100_eeprom_load: EEPROM corrupted" from dmesg. 

o@bluefish:~$ sudo modprobe -r e100
o@bluefish:~$ sudo modprobe e100 debug=15
o@bluefish:~$ dmesg | tail -100
[22495.493394] e100: Copyright(c) 1999-2006 Intel Corporation
[22495.495207] PCI: Found IRQ 5 for device 0000:00:0a.0
[22495.516868] e100: 0000:00:0a.0: mdio_ctrl: READ:addr=1, reg=0, data_in=0x0000, data_out=0x1820FFFF
[22495.516932] e100: 0000:00:0a.0: mdio_ctrl: READ:addr=1, reg=1, data_in=0x0000, data_out=0x1821FFFF
[...similar lines snipped out...]
[22495.522328] e100: 0000:00:0a.0: mdio_ctrl: READ:addr=31, reg=1, data_in=0x0000, data_out=0x1BE1FFFF
[22495.522387] e100: 0000:00:0a.0: mdio_ctrl: READ:addr=31, reg=1, data_in=0x0000, data_out=0x1BE1FFFF
[22495.522401] e100: 0000:00:0a.0: e100_phy_init: phy_addr = 31
[22495.565222] e100: eth1: e100_probe: addr 0xd7000000, irq 5, MAC addr 00:A0:C9:16:C0:26


So... what next?

---

### Post by djchandler on 2007-10-02
Please list the rest of the hardware specs for your system.

I would say your NIC isn't supported. What are the BIOS settings for PCI 2.1 compliance?

DJ

---

### Post by ofb on 2007-10-02
Everything's fine under Windows. Here's lshw. How do I find out the BIOS settings for PCI 2.1 compliance? (check the BIOS I guess -- EDIT: I don't have that option in BIOS.)

```
    description: Tower Computer
    product: System Name
    vendor: System Manufacturer
    version: System Version
    serial: SYS-1234567890
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: chassis=tower
  *-core
       description: Motherboard
       product: P3B-F
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: REV 1.01
       serial: xxxxxxxxxxx
       slot: SECONDARY IDE/HDD
     *-firmware
          description: BIOS
          vendor: Award Software, Inc.
          physical id: 0
          version: ASUS P3B-F ACPI BIOS Revision 1003.A (08/07/1999)
          size: 64KB
          capacity: 192KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi agp
     *-cpu
          description: CPU
          product: Pentium III (Katmai)
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.7.3
          slot: SLOT 1
          size: 450MHz
          capacity: 800MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse up
        *-cache:0
             description: L1 cache
             physical id: a
             slot: L1 Cache
             size: 32KB
             capacity: 32KB
             capabilities: pipeline-burst synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: b
             slot: L2 Cache
             size: 512KB
             capacity: 512KB
             capabilities: pipeline-burst synchronous internal write-back data
     *-memory
          description: System Memory
          physical id: 21
          slot: System board or motherboard
          size: 512MB
          capacity: 1GB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: DIMM 1
             size: 128MB
             width: 64 bits
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: DIMM 2
             size: 128MB
             width: 64 bits
        *-bank:2
             description: DIMM DRAM Synchronous
             physical id: 2
             slot: DIMM 3
             size: 128MB
             width: 64 bits
        *-bank:3
             description: DIMM DRAM Synchronous
             physical id: 3
             slot: DIMM 4
             size: 128MB
             width: 64 bits
     *-pci
          description: Host bridge
          product: 440BX/ZX/DX - 82443BX/ZX/DX Host bridge
          vendor: Intel Corporation
          physical id: e4000000
          bus info: pci@00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: latency=64
          resources: iomemory:e4000000-e7ffffff
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
                product: NV11 [GeForce2 MX/MX 400]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@01:00.0
                version: b2
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5
                resources: iomemory:d5000000-d5ffffff iomemory:d8000000-dfffffff irq:11
        *-isa
             description: ISA bridge
             product: 82371AB/EB/MB PIIX4 ISA
             vendor: Intel Corporation
             physical id: 4
             bus info: pci@00:04.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82371AB/EB/MB PIIX4 IDE
             vendor: Intel Corporation
             physical id: 4.1
             bus info: pci@00:04.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=PIIX_IDE latency=32
             resources: iomemory:1f0-1f7 iomemory:3f0-3ef iomemory:170-177 iomemory:370-36f ioport:d800-d80f
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk:0
                   description: ATA Disk
                   product: ST33221A
                   vendor: Seagate
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: 3.11
                   serial: GTP84570
                   size: 3077MB
                   capacity: 3077MB
                   capabilities: ata dma lba iordy smart pm partitioned partitioned:dos
                   configuration: mode=udma2 smart=on
                 *-volume:0
                      description: Linux filesystem partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 2886MB
                      capabilities: primary bootable
                 *-volume:1
                      description: Extended partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      size: 188MB
                      capacity: 188MB
                      capabilities: primary extended partitioned partitioned:extended
                    *-logicalvolume
                         description: Linux swap / Solaris partition
                         physical id: 5
                         logical name: /dev/hda5
                         capacity: 188MB
                         capabilities: nofs
              *-disk:1
                   description: ATA Disk
                   product: QUANTUM FIREBALL_TM2110A
                   vendor: Quantum
                   physical id: 1
                   bus info: ide@0.1
                   logical name: /dev/hdb
                   version: A6B.2400
                   serial: 394703260472
                   size: 2014MB
                   capacity: 2014MB
                   capabilities: ata dma lba iordy partitioned partitioned:dos
                 *-volume
                      description: W95 FAT32 partition
                      physical id: 1
                      bus info: ide@0.1,1
                      logical name: /dev/hdb1
                      capacity: 2014MB
                      capabilities: primary bootable
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom:0
                   description: IDE CD-ROM
                   product: ASUS CD-S520/A
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: 1.9K
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio
                   configuration: mode=udma2
                 *-disc
                      physical id: 0
                      logical name: /dev/hdc
              *-cdrom:1
                   description: CD-R/CD-RW writer
                   product: CREATIVE CD-RW RW4224E
                   physical id: 1
                   bus info: ide@1.1
                   logical name: /dev/hdd
                   version: 1.36
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw
                 *-disc
                      physical id: 0
                      logical name: /dev/hdd
        *-usb
             description: USB Controller
             product: 82371AB/EB/MB PIIX4 USB
             vendor: Intel Corporation
             physical id: 4.2
             bus info: pci@00:04.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=32
             resources: ioport:d400-d41f irq:9
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-bridge
             description: Bridge
             product: 82371AB/EB/MB PIIX4 ACPI
             vendor: Intel Corporation
             physical id: 4.3
             bus info: pci@00:04.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bridge
             configuration: driver=piix4_smbus latency=0
             resources: irq:9
        *-network:0
             description: Ethernet interface
             product: RTL-8029(AS)
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: 9
             bus info: pci@00:09.0
             logical name: eth0
             version: 00
             serial: 00:50:ba:cb:0e:35
             width: 32 bits
             clock: 33MHz
             capabilities: ethernet physical
             configuration: broadcast=yes driver=ne2k-pci driverversion=1.03 ip=24.69.23.71 latency=0 multicast=yes
             resources: ioport:d000-d01f irq:9
        *-network:1 DISABLED
             description: Ethernet interface
             product: 82557/8/9 [Ethernet Pro 100]
             vendor: Intel Corporation
             physical id: a
             bus info: pci@00:0a.0
             logical name: eth1
             version: 01
             serial: 00:a0:c9:16:c0:26
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI duplex=full firmware=N/A latency=32 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
             resources: iomemory:d7000000-d7000fff ioport:b800-b81f iomemory:d4800000-d48fffff irq:5
        *-multimedia
             description: Multimedia audio controller
             product: SB Live! EMU10k1
             vendor: Creative Labs
             physical id: b
             bus info: pci@00:0b.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=EMU10K1_Audigy latency=32 maxlatency=20 mingnt=2
             resources: ioport:b400-b41f irq:10
        *-input
             description: Input device controller
             product: SB Live! Game Port
             vendor: Creative Labs
             physical id: b.1
             bus info: pci@00:0b.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Emu10k1_gameport latency=32
             resources: ioport:b000-b007
```

---

### Post by Sand Lee on 2007-10-03
Have you recently updated the network driver? I had a similar problem that didn't get fixed until I rolled back the windows driver.

---

### Post by ofb on 2007-10-03
> **Sand Lee said:**
> Have you recently updated the network driver? I had a similar problem that didn't get fixed until I rolled back the windows driver.

It's a fresh install. I had the same trouble under Kubuntu 7.04 in the days before. 

Previously, the machine has never run Linux except as LiveCDs, and I never checked the second card under those.

But yes, it does sound like that sort of problem, and the out-dated fix I linked to looks like the 'try a similar driver' approach. I'd do that if I could figure one out.

There's a /lot/ of posts about Linux trouble with this card, but all seem to revolve around the out-dated fix, or people having the corrupt eeprom issue that I don't have.

---

### Post by ofb on 2007-10-04
I've been playing with LiveCDs to see if I can learn anything. I can ping the card from my other box when using Puppy Linux, and the old Suse 8.0 eval.

Unfortunately neither of those distros has handy commands like lshw or ethtool or even ifdown. 

Suse uses the /etc/modules.conf file, and shows 'alias eth1 e100'.

I've no idea what Puppy is using. They've got that distro really stripped down. All I found was the file /etc/networkmodules, which has a long list that includes: e100 "pci:  Intel(R) PRO/100 Network Driver"

... and, I really don't know what to do with this discovery.  What's different about the Ubuntu distros that keeps the card from being enabled?

---

### Post by ofb on 2007-10-04
interesting... where's eth1?

cat /proc/interrupts

           CPU0
  0:      31410    XT-PIC-XT        timer
  1:         57    XT-PIC-XT        i8042
  2:          0    XT-PIC-XT        cascade
  6:          5    XT-PIC-XT        floppy
  7:          1    XT-PIC-XT        parport0
  8:          3    XT-PIC-XT        rtc
  9:         21    XT-PIC-XT        acpi, uhci_hcd:usb1, eth0
 10:          0    XT-PIC-XT        EMU10K1
 11:       5333    XT-PIC-XT        nvidia
 12:       1443    XT-PIC-XT        i8042
 14:       5505    XT-PIC-XT        ide0
 15:       1470    XT-PIC-XT        ide1
NMI:          0
LOC:          0
ERR:          0
MIS:          0

EDIT: For that matter, where is irq5? That's what the other information shows eth1 is using.

---

### Post by ofb on 2007-10-04
Curiouser and curiouser...

o@bluefish:~$ dmesg | grep e100
[   50.200023] PCI: Firmware left 0000:00:0a.0 e100 interrupts enabled, disabling
[   57.957498] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k2-NAPI
[   57.957514] e100: Copyright(c) 1999-2006 Intel Corporation
[   11.684000] e100: eth1: e100_probe: addr 0xd7000000, irq 5, MAC addr 00:A0:C9:16:C0:26

Why does Ubuntu disable it?

And is there any way I can stop it doing that, at least as an experiment?

FWIW, I've tried replacing e100 with the older blacklisted eepro100, and all sorts of PCI related add-ons to the boot message like pci=irqpoll, and of course digging around in BIOS. And I flashed the BIOS.

EDIT - Hey, I /do/ have PCI 2.1 compliance in the BIOS. Missed that. It's ENABLED, and yup I tried DISABLED with no change.

---

### Post by ofb on 2007-10-04
For nothing better to do, I tried a different slot. This didn't fix anything of course, but most surprisingly it did create a new entry. Compare the 'dmesg | grep disa' of Before and After below.


o@bluefish:~$ cat /proc/interrupts
           CPU0       
  0:      25388    XT-PIC-XT        timer
  1:         29    XT-PIC-XT        i8042
  2:          0    XT-PIC-XT        cascade
  6:          5    XT-PIC-XT        floppy
  7:          1    XT-PIC-XT        parport0
  8:          3    XT-PIC-XT        rtc
  9:         22    XT-PIC-XT        acpi, uhci_hcd:usb1, eth0
 10:          0    XT-PIC-XT        EMU10K1
 11:       3278    XT-PIC-XT        nvidia
 12:        559    XT-PIC-XT        i8042
 14:       5054    XT-PIC-XT        ide0
 15:       1026    XT-PIC-XT        ide1
NMI:          0 
LOC:          0 
ERR:          0
MIS:          0
o@bluefish:~$ dmesg | grep disa
[   45.340763] Local APIC disabled by BIOS -- you can enable it with "lapic"
[   46.942176] PCI: Firmware left 0000:00:0a.0 e100 interrupts enabled, disabling
[   46.992134]   IO window: disabled.
[   49.691218] audit: initializing netlink socket (disabled)



o@bluefish:~$ cat /proc/interrupts
           CPU0       
  0:      25892    XT-PIC-XT        timer
  1:         53    XT-PIC-XT        i8042
  2:          0    XT-PIC-XT        cascade
  5:         20    XT-PIC-XT        uhci_hcd:usb1, eth0
  6:          5    XT-PIC-XT        floppy
  7:          1    XT-PIC-XT        parport0
  8:          3    XT-PIC-XT        rtc
  9:          0    XT-PIC-XT        acpi
 10:          0    XT-PIC-XT        EMU10K1
 11:       3462    XT-PIC-XT        nvidia
 12:        583    XT-PIC-XT        i8042
 14:       5059    XT-PIC-XT        ide0
 15:       1063    XT-PIC-XT        ide1
NMI:          0 
LOC:          0 
ERR:          0
MIS:          0
o@bluefish:~$ dmesg | grep disa
[   47.892417] Local APIC disabled by BIOS -- you can enable it with "lapic"
[   49.489538] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   49.493892] PCI: Firmware left 0000:00:0d.0 e100 interrupts enabled, disabling
[   49.543746]   IO window: disabled.
[   52.242909] audit: initializing netlink socket (disabled)


In the 'new' configuration, the two cards ended up on slots 4 and 5, which is the same thing to this BIOS, and both cards were assigned IRQ 5. Again, the e100 was disabled by Ubuntu, but check out that 'ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.'  Why has that shown up?

Incidently, see: 'Local APIC disabled by BIOS -- you can enable it with "lapic"' I have tried adding lapic to boot of course. Nothing changed -- and by that I mean /nothing/ changed; I still got that message. Very odd.

---

### Post by ofb on 2007-10-06
Okay... 

o@bluefish:~$ sudo rmmod e100
o@bluefish:~$ sudo modprobe eepro100

That actually works. 

I'd tried to do that early by removing eepro100 in the blacklist,  placing e100 there, & rebooting. But without success, so I thought the older driver didn't work either.

Okay, eepro100 makes the card work in Ubuntu 7.04. Yay. But eepro100 /is/ blacklisted for some reason. Doing this swap can't be good. What trouble am I setting myself up for?

```
o@bluefish:~$ dmesg
(new lines only)

[  172.772000] eth1: 0000:00:0a.0, 00:A0:C9:16:C0:26, IRQ 5.
[  172.772000]   Receiver lock-up bug exists -- enabling work-around.
[  172.772000]   Board assembly 645477-004, Physical connectors present: RJ45 BNC AUI
[  172.772000]   Primary interface chip 80c24 PHY #0.
[  172.772000]   General self-test: passed.
[  172.772000]   Serial sub-system self-test: passed.
[  172.772000]   Internal registers self-test: passed.
[  172.772000]   ROM checksum self-test: passed (0x49caa8d6).
[  172.772000]   Receiver lock-up workaround activated.
[  183.436000] eth1: no IPv6 routers present
[  218.984000] Inbound IN=eth0 OUT= MAC=00:50:ba:cb:0e:35:00:00:77:94:69:18:08:00 SRC=24.69.166.161 DST=24.69.23.71 LEN=48 TOS=0x00 PREC=0x00 TTL=125 ID=49436 DF PROTO=TCP SPT=2557 DPT=445 WINDOW=64240 RES=0x00 SYN URGP=0 
[  221.812000] Inbound IN=eth0 OUT= MAC=00:50:ba:cb:0e:35:00:00:77:94:69:18:08:00 SRC=24.69.166.161 DST=24.69.23.71 LEN=48 TOS=0x00 PREC=0x00 TTL=125 ID=51702 DF PROTO=TCP SPT=2557 DPT=445 WINDOW=64240 RES=0x00 SYN URGP=0 


o@bluefish:~$ cat /proc/interrupts
           CPU0       
  0:     191926    XT-PIC-XT        timer
  1:        507    XT-PIC-XT        i8042
  2:          0    XT-PIC-XT        cascade
  5:        334    XT-PIC-XT        eth1
  6:          5    XT-PIC-XT        floppy
  7:          1    XT-PIC-XT        parport0
  8:          3    XT-PIC-XT        rtc
  9:       1550    XT-PIC-XT        acpi, uhci_hcd:usb1, eth0
 10:          0    XT-PIC-XT        EMU10K1
 11:      60561    XT-PIC-XT        nvidia
 12:      35639    XT-PIC-XT        i8042
 14:       7375    XT-PIC-XT        ide0
 15:      13347    XT-PIC-XT        ide1
NMI:          0 
LOC:          0 
ERR:          0
MIS:          0


o@bluefish:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: RTL-8029(AS)
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@00:09.0
       logical name: eth0
       version: 00
       serial: 00:50:ba:cb:0e:35
       width: 32 bits
       clock: 33MHz
       capabilities: ethernet physical
       configuration: broadcast=yes driver=ne2k-pci driverversion=1.03 ip=24.69.23.71 latency=0 multicast=yes
       resources: ioport:d000-d01f irq:9
  *-network:1
       description: Ethernet interface
       product: 82557/8/9 [Ethernet Pro 100]
       vendor: Intel Corporation
       physical id: a
       bus info: pci@00:0a.0
       logical name: eth1
       version: 01
       serial: 00:a0:c9:16:c0:26
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=eepro100 driverversion=eepro100.c:v1.09j-t 9/29/99 Don duplex=full ip=192.168.0.2 latency=32 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: iomemory:d7000000-d7000fff ioport:b800-b81f iomemory:d4800000-d48fffff irq:5
```

Now to try to make that permanent. I suppose by the /etc/modprobe.d/blacklist, since that's the only reference to them.

EDIT:

Well, fudge. That does not, in fact, make the change permanent. 

What I get on reboot is the same e100 troubles in dmesg, plus another couple of lines about eepro100. Ubuntu seems to load them both. The result is right back to the old business with no IRQ 5, and ETH1 DISABLED. Running rmmod and modprobe does not fix things under this configuration.

Remove my attempts at blacklisting, reboot, then run rmmod and modprobe, and success again.

So how do I make it permanent then? Ubuntu 7.04 does not handle blacklisting like earlier versions, so I'm not finding useful information online.

---

### Post by ofb on 2007-10-07
Right, then. This is a fudge to help anyone else with the trouble.

sudo nano /etc/rc.local

Add the following line before the 'exit 0' line,

modprobe -r e100 && modprobe eepro100


What that does: After startup, the e100 driver is removed, and the eepro100 driver is installed.


Outstanding issues:

1) I don't know why I can't achieve that using the /etc/modprobe.d files

2) I don't know why I need to use the obsolete driver with kernel 2.6

---

### Post by Whiffle on 2007-10-07
Have you tried passing "noapic" to the kernel at boot?

[http://ubuntuforums.org/showthread.php?p=159853](http://ubuntuforums.org/showthread.php?p=159853)

---

### Post by ofb on 2007-10-07
Yup. with and without 'nolapic', plus a few other boot additions that people have tried in the past.

---

