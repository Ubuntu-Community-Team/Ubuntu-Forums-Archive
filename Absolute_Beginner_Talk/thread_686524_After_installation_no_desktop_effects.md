---
title: "After installation no desktop effects"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by bprof on 2008-02-03
Hi,

After I installed Ubuntu 7.10 the desktop effects were gone, they worked just fine from the LiveCD. Is there any reason for that? Is there anything I can do to get desktop effects work?

Thank you,

---

### Post by forestpixie on 2008-02-03
make sure you have driver installed for you graphics card, restricted drivers - then enable in system > preferences >appearance

to control properly install ccsm

sudo apt-get install compizconfig-settings-manager

---

### Post by jan quark on 2008-02-03
please post your specs by

running
```

lspci
```
```

lshw
```

---

### Post by bprof on 2008-02-04
Here is the result of running lspci

```
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82562V-2 10/100 Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
```

And here is the result for running lshw:

```
hylobatidae
    description: Desktop Computer
    product: Vostro 200
    vendor: Dell Inc.
    version: OEM
    serial: 784CBF1
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5
    configuration: boot=normal chassis=desktop uuid=44454C4C-3800-1034-8043-B7C04F424631
  *-core
       description: Motherboard
       product: 0CU409
       vendor: Dell Inc.
       physical id: 0
       serial: ..CN736047B903W1.
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: 1.0.5 (09/14/2007)
          size: 128KB
          capacity: 1984KB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) Dual  CPU  E2140  @ 1.60GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          slot: Socket 775
          size: 1600MHz
          capacity: 4GHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 32KB
             capacity: 32KB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: b
             slot: External Cache
             size: 1MB
             capacity: 1MB
             capabilities: synchronous external write-back
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 24
          slot: System board or motherboard
          size: 2GB
        *-bank:0
             description: DIMM Synchronous 667 MHz (1.5 ns)
             product: 64T128020HU3SB
             vendor: 7F7F7F7F7F510000
             physical id: 0
             serial: 06308B16
             slot: DIMM1
             size: 1GB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM [empty]
             product: 64T64000HU25FB
             vendor: 7F7F7F7F7F510000
             physical id: 1
             serial: 010AFE20
             slot: DIMM2
        *-bank:2
             description: DIMM Synchronous 667 MHz (1.5 ns)
             product: 64T128020HU3SB
             vendor: 7F7F7F7F7F510000
             physical id: 2
             serial: 06308C17
             slot: DIMM3
             size: 1GB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:3
             description: DIMM [empty]
             product: 64T64000HU25FB
             vendor: 7F7F7F7F7F510000
             physical id: 3
             serial: 010B0424
             slot: DIMM4
     *-pci
          description: Host bridge
          product: 82G33/G31/P35/P31 Express DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-pci:0
             description: PCI bridge
             product: 82G33/G31/P35/P31 Express PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-display
             description: VGA compatible controller
             product: 82G33/G31 Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm vga bus_master cap_list
             configuration: latency=0
        *-network
             description: Ethernet interface
             product: 82562V-2 10/100 Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 02
             serial: 00:1d:09:7d:23:c8
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000-ich9 driverversion=7.6.5-NAPI duplex=full firmware=1.1-2 ip=192.168.0.235 latency=0 link=yes module=e1000_ich9 multicast=yes port=twisted pair speed=100MB/s
        *-usb:0
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-usb:4
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:5
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:6
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:7
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 92
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: 82801IR (ICH9R) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk
                description: SCSI Disk
                product: ST380815AS
                vendor: ATA
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 3.AD
                serial: 5RW1CVBC
                size: 74GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: Dell Utility partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 39MB
                   capabilities: primary
              *-volume:1
                   description: HPFS/NTFS partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   capacity: 10GB
                   capabilities: primary
              *-volume:2
                   description: HPFS/NTFS partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   capacity: 32GB
                   capabilities: primary bootable
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   size: 32GB
                   capacity: 32GB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 30GB
                      capabilities: bootable
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 1404MB
                      capabilities: nofs
           *-cdrom
                description: DVD reader
                product: DVD-ROM TS-H353B
                vendor: TSSTcorp
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: D200
                capabilities: removable audio dvd
                configuration: ansiversion=5 status=open
        *-serial UNCLAIMED
             description: SMBus
             product: 82801I (ICH9 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
        *-ide:1
             description: IDE interface
             product: 82801I (ICH9 Family) 2 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0 module=ata_piix
```

Thank you for helping me out with this issue.

---

### Post by billgoldberg on 2008-02-04
Like others say:

Enable your graphic card's driver in the  restriced drivers manager.

Then download ccsm (using the commandline or by going to system > administration > synaptic package manager and searching for "compizconfig", then installing the first one).

Then go to system > preferences > appearance.

On the visual effects tab select costum.

Then go to system > preferences > advanced desktop effects setting

and enable the special effects you want.

If you encouter any problems, post then in the beginners forum.

---

### Post by FuturePilot on 2008-02-04
I don't think there is a restricted driver for Intel cards.

---

### Post by bprof on 2008-02-04
I've check the restricted manager, and display card is not there. Is there something else I should do for the card to work?

Thank you,

---

### Post by FuturePilot on 2008-02-04
Can you post the output of
```
compiz --replace
```

---

### Post by corney91 on 2008-02-04
> **FuturePilot said:**
> I don't think there is a restricted driver for Intel cards.
I didn't think so either

> **bprof said:**
> I've check the restricted manager, and display card is not there. Is there something else I should do for the card to work?

Thank you,
Is there nothing in the 'Visual Effects' tab in Appearance (System > Preferences)?

---

### Post by bprof on 2008-02-06
FuturePilot, here is what I got after running 

```
#compiz --replace
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

```

corney91, In the visual tab I can see four selections:

None
Normal
Extra
Custom

Thank you,

---

### Post by Crumpets and Jam on 2008-02-06
> **bprof said:**
> FuturePilot, here is what I got after running 

```
#compiz --replace
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

```

corney91, In the visual tab I can see four selections:

None
Normal
Extra
Custom

Thank you,

Install XGL.

```
sudo apt-get install xserver-xgl
```

---

### Post by bprof on 2008-02-06
I've installed XGL but still getting this message:
> 
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

Thank you,

---

### Post by FuturePilot on 2008-02-06
Did you logout and back in?

---

### Post by Crumpets and Jam on 2008-02-06
> **bprof said:**
> I've installed XGL but still getting this message:


Thank you,

Yeah, try a restart.

---

### Post by bprof on 2008-02-06
I did, and it gave me just after I logged in a message that it will start for this user automatically. But am still getting the same error:
> 
Checking for Xgl: not present.
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

---

### Post by bprof on 2008-02-07
Any help, please!

---

### Post by adster101 on 2008-02-07
I just installed Xgl and my system seems a lot quicker now. Only been using it for about 3 months as it was and I thought it was just a bit slower than Windows. However, Xgl seem to have really speeded things up.

After you install you also need to change you session on the sign in page to Gnome failsafe or somthing similar. This stops any start up scripts running when you boot up and Xgl seems to run fine for me.

:)

---

### Post by bprof on 2008-02-08
Thank you adster101 I've tried what you said, now I got this message:

> aborting and using fallback: /usr/bin/metacity 

???

---

### Post by adster101 on 2008-02-11
No sorry, actually it seems that Xgl is not necessary depending on which drivers you are using to power your graphics card. 

Hang on and I will post a link to the other thread...

---

### Post by adster101 on 2008-02-12
Hi bprof,

See this thread in which I posted a similar problem. 

It seems as though you might need to uninstall the fglrx proprietry drivers to get the ati driver working. 

See if this helps:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Thanks

---

