---
title: "[SOLVED] no sound"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by Tyke91 on 2007-09-22
So, my dad finally caved in and now he's got ubuntu on his computer as well (i've finally 'converted' my entire family :D )

his computer, unlike mine and my moms has failed to auto configure any type of sound at all. I've tried forum searches and solutions... i've downloaded and compiled the latest alsa drivers, and i've read tutorials... but i still can't get this damn thing working. When i go into the alsa mixer, all I see is one bar and it is all the way up. When a sound should be playing, all I hear is a very very faint crackling sound.

what is going on?

---

### Post by reckless2k2 on 2007-09-22
hey......with all those beans you really should know you have to give some more details. hahaha. let's at least have some pc info.

---

### Post by Tyke91 on 2007-09-22
hehe. i would, but unfortunately there is something going on where i can only log on to the ubuntu forums from MY computer... every time i log on somewhere else (even if i'm logged off here) i get kicked off my acount before i can post... that being the case, it's kinda hard to copy/paste system specs... so i was hoping for a sort of generic solution :)

i'll see what i can do tho (will be emailing myself the specs momentarily)

---

### Post by Tyke91 on 2007-09-22
meh... finally logged on here by resetting my password...

anyway... system specs

```
Password:
ken-ubuntu                
    description: Space-saving Computer
    product: Dell DXC051
    vendor: Dell Inc.
    serial: C9FLM81
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: administrator_password=enabled boot=normal chassis=space-saving power-on_password=enabled uuid=44454C4C-3900-1046-804C-C3C04F4D3831
  *-core
       description: Motherboard
       product: 0DD431
       vendor: Dell Inc.
       physical id: 0
       serial: ..CN6986158F0702.
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: A01 (09/06/2005)
          size: 64KB
          capacity: 448KB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect edd int13floppytoshiba int5printscreen int9keyboard int14serial int17printer acpi usb ls120boot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 3.00GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 15.4.3
          serial: 0000-0F43-0000-0000-0000-0000
          slot: Microprocessor
          size: 3GHz
          capacity: 4GHz
          width: 64 bits
          clock: 800MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pni monitor ds_cpl est cid cx16 xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 16KB
             capacity: 16KB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 2MB
             capacity: 2MB
             capabilities: internal varies unified
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
          physical id: 1000
          slot: System board or motherboard
          size: 1GB
          capacity: 1GB
        *-bank:0
             description: DIMM DDR Synchronous 533 MHz (1.9 ns)
             product: 64T64000HU3.7A
             vendor: C100000000000000
             physical id: 0
             serial: 03012527
             slot: DIMM_1
             size: 512MB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:1
             description: DIMM DDR Synchronous 533 MHz (1.9 ns) [empty]
             vendor: FFFFFFFFFFFFFFFF
             physical id: 1
             serial: FFFFFFFF
             slot: DIMM_3
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:2
             description: DIMM DDR Synchronous 533 MHz (1.9 ns)
             product: 64T64000HU3.7A
             vendor: C100000000000000
             physical id: 2
             serial: 03012422
             slot: DIMM_2
             size: 512MB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:3
             description: DIMM DDR Synchronous 533 MHz (1.9 ns) [empty]
             vendor: FFFFFFFFFFFFFFFF
             physical id: 3
             serial: FFFFFFFF
             slot: DIMM_4
             width: 64 bits
             clock: 533MHz (1.9ns)
     *-pci
          description: Host bridge
          product: 82945G/GZ/P/PL Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82945G/GZ/P/PL PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-display:0
                description: VGA compatible controller
                product: RV380 [Radeon X600 (PCIE)]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@01:00.0
                version: 00
                size: 128MB
                width: 64 bits
                clock: 33MHz
                capabilities: vga bus_master cap_list
                configuration: latency=0
                resources: iomemory:e0000000-e7ffffff iomemory:efde0000-efdeffff ioport:dc00-dcff irq:16
           *-display:1 UNCLAIMED
                description: Display controller
                product: RV380 [Radeon X600]
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@01:00.1
                version: 00
                size: 64KB
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=0
                resources: iomemory:efdf0000-efdfffff
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: iomemory:efffc000-efffffff irq:16
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:ff80-ff9f irq:18
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:ff60-ff7f irq:19
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:ff40-ff5f irq:20
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb:0
                   description: Keyboard
                   product: Dell USB Keyboard
                   vendor: Dell
                   physical id: 1
                   bus info: usb@4:1
                   version: 3.50
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=70mA speed=1.5MB/s
              *-usb:1
                   description: Mouse
                   product: Dell USB Mouse
                   vendor: Dell
                   physical id: 2
                   bus info: usb@4:2
                   version: 1.10
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:ff20-ff3f irq:21
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: iomemory:ffa80800-ffa80bff irq:18
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.20-16-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s
        *-pci:2
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-network
                description: Ethernet interface
                product: 82801G (ICH7 Family) LAN Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@03:08.0
                logical name: eth0
                version: 01
                serial: 00:12:3f:a7:90:72
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI duplex=full firmware=N/A ip=192.168.0.100 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
                resources: iomemory:efbfb000-efbfbfff ioport:ccc0-ccff irq:17
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
                vendor: Texas Instruments
                physical id: a
                bus info: pci@03:0a.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2
                resources: iomemory:efbfa800-efbfafff iomemory:efbfc000-efbfffff irq:20
        *-isa
             description: ISA bridge
             product: 82801GH (ICH7DH) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@00:1f.1
             logical name: scsi4
             logical name: scsi5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated scsi-host
             configuration: driver=ata_piix latency=0
             resources: ioport:1f0-1f7 ioport:3f4-3f3 ioport:170-177 ioport:374-373 ioport:ffa0-ffaf irq:16
           *-cdrom
                description: DVD reader
                product: CDRW/DVD TSL462C
                vendor: TSSTcorp
                physical id: 0.0.0
                bus info: scsi@4:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: DE01
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5
              *-disc
                   physical id: 0
                   logical name: /dev/cdrom
        *-storage
             description: SATA controller
             product: 82801GR/GH (ICH7 Family) Serial ATA Storage Controller AHCI
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@00:1f.2
             logical name: scsi0
             logical name: scsi1
             logical name: scsi2
             logical name: scsi3
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list emulated scsi-host
             configuration: driver=ahci latency=0
             resources: ioport:fe00-fe07 ioport:fe10-fe13 ioport:fe20-fe27 ioport:fe30-fe33 ioport:fea0-feaf iomemory:efffbc00-efffbfff irq:17
           *-disk
                description: SCSI Disk
                product: ST3160023AS
                vendor: ATA
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 8.12
                serial: 5MT2AB4N
                size: 149GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: Dell Utility partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 31MB
                   capabilities: primary
              *-volume:1
                   description: HPFS/NTFS partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   capacity: 93GB
                   capabilities: primary bootable
              *-volume:2
                   description: CP/M / CTOS / ... partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   capacity: 4855MB
                   capabilities: primary
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   size: 51GB
                   capacity: 51GB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 47GB
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 3671MB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:ece0-ecff irq:9




```
```
ken@ken-ubuntu:~$ sudo lshw -businfo
Bus info        Device      Class       Description
===================================================
                            system      Dell DXC051
                            bus         0DD431
                            memory      BIOS
cpu@0                       processor   Intel(R) Pentium(R) 4 CPU 3.00GHz
                            memory      L1 cache
                            memory      L2 cache
                            processor   Logical CPU
                            processor   Logical CPU
                            memory      System Memory
                            memory      64T64000HU3.7A
                            memory      DIMM DDR Synchronous 533 MHz (1.9 ns) [e
                            memory      64T64000HU3.7A
                            memory      DIMM DDR Synchronous 533 MHz (1.9 ns) [e
pci@00:00.0                 bridge      82945G/GZ/P/PL Memory Controller Hub
pci@00:01.0                 bridge      82945G/GZ/P/PL PCI Express Root Port
pci@01:00.0                 display     RV380 [Radeon X600 (PCIE)]
pci@01:00.1                 display     RV380 [Radeon X600]
pci@00:1b.0                 multimedia  82801G (ICH7 Family) High Definition Aud
pci@00:1c.0                 bridge      82801G (ICH7 Family) PCI Express Port 1
pci@00:1d.0                 bus         82801G (ICH7 Family) USB UHCI #1
usb@2           usb2        bus         UHCI Host Controller
pci@00:1d.1                 bus         82801G (ICH7 Family) USB UHCI #2
usb@3           usb3        bus         UHCI Host Controller
pci@00:1d.2                 bus         82801G (ICH7 Family) USB UHCI #3
usb@4           usb4        bus         UHCI Host Controller
usb@4:1                     input       Dell USB Keyboard
usb@4:2                     input       Dell USB Mouse
pci@00:1d.3                 bus         82801G (ICH7 Family) USB UHCI #4
usb@5           usb5        bus         UHCI Host Controller
pci@00:1d.7                 bus         82801G (ICH7 Family) USB2 EHCI Controlle
usb@1           usb1        bus         EHCI Host Controller
pci@00:1e.0                 bridge      82801 PCI Bridge
pci@03:08.0     eth0        network     82801G (ICH7 Family) LAN Controller
pci@03:0a.0                 bus         TSB43AB22/A IEEE-1394a-2000 Controller (
pci@00:1f.0                 bridge      82801GH (ICH7DH) LPC Interface Bridge
pci@00:1f.1     scsi4       storage     82801G (ICH7 Family) IDE Controller
scsi@4:0.0.0    /dev/cdrom  disk        CDRW/DVD TSL462C
                /dev/cdrom  disk        
pci@00:1f.2     scsi0       storage     82801GR/GH (ICH7 Family) Serial ATA Stor
scsi@0:0.0.0    /dev/sda    disk        ST3160023AS
scsi@0:0.0.0,1  /dev/sda1   disk        Dell Utility partition
scsi@0:0.0.0,2  /dev/sda2   disk        HPFS/NTFS partition
scsi@0:0.0.0,3  /dev/sda3   disk        CP/M / CTOS / ... partition
scsi@0:0.0.0,4  /dev/sda4   disk        Extended partition
                /dev/sda5   disk        Linux filesystem partition
                /dev/sda6   disk        Linux swap / Solaris partition
pci@00:1f.3                 bus         82801G (ICH7 Family) SMBus Controller

```

---

### Post by reckless2k2 on 2007-09-22
just throwing it up on the wall to see if it sticks but have yout ried alsaconf from the cli?

---

### Post by w4ett on 2007-09-22
This post has some solutions for that chipset:

[http://ubuntuforums.org/archive/index.php/t-415363.html](http://ubuntuforums.org/archive/index.php/t-415363.html)

---

### Post by Tyke91 on 2007-09-22
hmm... following that link actually made things a little worse... now it does not see a sound card at all AND the volume control is "x"ed out.

>  		just throwing it up on the wall to see if it sticks but have yout ried alsaconf from the cli?

learn a little every day :) unfortunately, that didn't help... but it's nice to know that it's there.

---

### Post by w4ett on 2007-09-22
Just thought I'd throw out those results.......I've been using a beta search engine....here is some additional results....this search also covers the wikis and documentation.

[http://us.cypherbios.org/index.htm?cof=FORID:11&cx=002072379199720138921:9m-bgfzutzq&q=82801G+(ICH7+Family)+High+Definition+Audio+Controller#1114](http://us.cypherbios.org/index.htm?cof=FORID:11&cx=002072379199720138921:9m-bgfzutzq&q=82801G+(ICH7+Family)+High+Definition+Audio+Controller#1114)

---

### Post by Tyke91 on 2007-09-22
hmm... still nothing.

i'll sleep on it and try again in the morning

---

### Post by Tyke91 on 2007-09-23
alright, i think these two problems are linked.

one: the sound card in my dad's computer is no longer detected after following We4tt's advice. the system thinks it has a card active, but when you go to aplay -l it just shows you this ```
ken@ken-ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
ken@ken-ubuntu:~$

```

two: the game Neverwinter Nights refuses to start. I've noticed this problem on my computer a few times ONLY when the sound card has been previously in use, so i think the computer is stuck into believing a sound card is always in use, even though it doesn't actually see one.

this computer DOES have a sound card, sounds work on windows.

---

### Post by Tyke91 on 2007-09-23
typing the aplay command into the terminal results in the error message "no PCM device"

is there anything i can do?

---

### Post by Tyke91 on 2007-09-23
*bump ):P*

---

### Post by w4ett on 2007-09-23
May I suggest this tutorial for debugging sound problems?

[https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems)

---

### Post by Tyke91 on 2007-09-23
i did see that tutorial a while ago... but i got stuck on this step

```

**Manual installation of sound drivers**

  Now figure out which module you need go to [[IMG]https://help.ubuntu.com/htdocs/ubuntu/img/u-www.png[/IMG] Sound Drivers]("http://www.alsa-project.org/main/index.php/Matrix:Main") and pick the manufacturer.  With the information provided by previous commands it should be easy to find the right module. 
 To see if this module is available on your system (it usually is) try the following command:  
 $ modinfo [modulename]
This will also list the possible parameters for the module. For example some ISA cards require you to pass isapnp=0 to modprobe. It may also require the IRQ and IO of the card if that's the case, these can be found in the output of the aadebug script. 
 Now that you've figured out all this information, lets try loading the module  
 #modprobe example
$ sudo modprobe snd_es18xx isapnp=0 port=0x220 mpu_port=0x330 dma1=1 dma2=5 irq=5 fm_port=0x388
If this doesn't return any errors, we can save the parameters.  
 $ echo options [module-name] [module-options] | sudo tee /etc/modprobe.d/[module-name]
Now we can test our setup  
 #aplay should now list your sound card
root@ubuntu:/etc # aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ES1878 [ESS AudioDrive ES1878], device 0: ES1878 [ESS AudioDrive ES1878]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
#the speaker should beep
```

i don't see the sound card for the comp on the wiki list at all
$ /usr/bin/speaker-test

---

### Post by Tyke91 on 2007-09-23
k... i've determined that this sound card is an Intel with an ICH7 chipset... but how do i find the module?

---

### Post by Pumalite on 2007-09-23
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by Tyke91 on 2007-09-23
That howto also depends on knowing what kind of module you have... which i still don't know yet. can someone tell me how i can find out?

---

### Post by Tyke91 on 2007-09-23
It must have been a bad install, i reinstalled ubuntu and now it works perfectly :D

---

