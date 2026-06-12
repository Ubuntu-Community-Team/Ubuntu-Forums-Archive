---
title: "Compal FL90 laptop, sound issued"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by Ulfursson on 2007-10-19
OK, now that I have Ubuntu installed (thanks to everyone who helped me with the partitioning, wireless set-up and everything else, btw), I'd like to get the sound working. Someone noted I may need to take care of this after the installation, so here I am.

---

### Post by Pumalite on 2007-10-19
Sound:

[http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound+problem+solutions+guide](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound+problem+solutions+guide)

[https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems)

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

[http://www.alsa-project.org/main/index.php/MainPage](http://www.alsa-project.org/main/index.php/MainPage)

If it doesn't work go to [http://www.alsa-project.org/main/index.php/MainPage](http://www.alsa-project.org/main/index.php/MainPage), download the
alsa-driver, lib and utils and follow the Howto at the same address and look for your driver at the Sound card matrix. Then, if needed, apply the patch and add something at the end of /etc/modprobe.d/alsa-base (sudo gedit) at described in the previous link. I do not own the same laptop but I also have got a Intel Sound Card and worked a bit to have a functioning audio.
I hope it will help you

After fiddling with the sound settings trying various suggestions in the Comprehensive Sound Problem Solutions Guide thread, I totally buggered up my sound. Oh well, a fresh install of Feisty never hurt anyone and I had my /home directory on a separate partition.

After the new install, I still had the 6 symptoms described above.

Thinking that it might be some sort of .config file remnant, I created a new user and everythng worked properly. A-HA! Comparing the user home directories, I noticed the presence of a .asoundrc file and another similarly named file. After doing some research here about what the file is for (and it's safe removal), I deleted it, logged out and returned to a system with full working sound.

My suggestion is this:

1. Create a new user account
2. Login using new user account
3. Check to see if sound works properly
4. If it does, then the issue is likely some sort of config file. Look for the .asoundrc file in your original home directory and move it to a backup folder (just in case)
5. Log back in as your original user and test.
6. If it fails to cure the problem, try the Comprehensive Guide above.

---

### Post by Ulfursson on 2007-10-19
bump back to page 1

---

### Post by Ulfursson on 2007-10-20
OK, I've followed the instructions on [http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel](http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel) . Everything seemed to go fine, and after I restarted there is a red sign next to the volume control icon. When I try to access volume control, I get the message, "No volume control GStreamer plugins and/or devices found. What should I do now?

---

### Post by Pumalite on 2007-10-20
It seems your kernel is not mounting the module for your sound card, (not recognizing it)
Post:
lshw

---

### Post by Ulfursson on 2007-10-20
```
eyjolf@ANDLANG:~$ sudo lshw
[sudo] password for eyjolf:
andlang                   
    description: Notebook
    product: N/A
    vendor: -
    version: N/A
    serial: N/A
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=oem-specific chassis=notebook uuid=78C34E97-0ACA-11DC-B017-0016D4DCBFF1
  *-core
       description: Motherboard
       product: IFL90
       vendor: COMPAL
       physical id: 0
       version: REFERENCE
       serial: N/A
     *-firmware
          description: BIOS
          vendor: COMPAL
          physical id: 0
          version: 1.07 (05/11/2007)
          size: 103KB
          capacity: 960KB
          capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     T7100  @ 1.80GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          slot: U2E1
          size: 1801MHz
          capacity: 4096MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe x86-64 constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 64KB
             capacity: 64KB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 2MB
             capacity: 4MB
             capabilities: burst internal write-back
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
          physical id: d
          slot: System board or motherboard
          size: 2GB
        *-bank:0
             description: SODIMM Synchronous 667 MHz (1.5 ns)
             product: SODIMM000
             vendor: Mfg 0
             physical id: 0
             serial: 1234-B0
             slot: M1
             size: 1GB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: SODIMM Synchronous 667 MHz (1.5 ns)
             product: SODIMM001
             vendor: Mfg 1
             physical id: 1
             serial: 1234-B1
             slot: M2
             size: 1GB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-pci
          description: Host bridge
          product: Mobile PM965/GM965/GL960 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 0c
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile PM965/GM965/GL960 PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 0c
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: GeForce 8600M GT
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga bus_master cap_list
                configuration: driver=nvidia latency=0 module=nvidia
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Contoller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-multimedia UNCLAIMED
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: latency=0
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: NetLink BCM5787M Gigabit Ethernet PCI Express
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: eth0
                version: 02
                serial: 00:16:d4:dc:bf:f1
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.77 latency=0 link=no module=tg3 multicast=yes port=twisted pair
        *-pci:3
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:4
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:5
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:6
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: PRO/Wireless 4965 AG or AGN Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:0c:00.0
                logical name: wmaster0
                version: 61
                serial: 00:13:e8:26:7c:ed
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=iwl4965 ip=192.168.2.4 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:7
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f3
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 6
                bus info: pci@0000:0e:06.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2 module=ohci1394
           *-system:0
                description: Generic system peripheral
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 6.1
                bus info: pci@0000:0e:06.1
                version: 22
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci latency=64 module=sdhci
           *-system:1 UNCLAIMED
                description: System peripheral
                product: R5C843 MMC Host Controller
                vendor: Ricoh Co Ltd
                physical id: 6.2
                bus info: pci@0000:0e:06.2
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: pm cap_list
                configuration: latency=64
           *-system:2 UNCLAIMED
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 6.3
                bus info: pci@0000:0e:06.3
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: pm cap_list
                configuration: latency=64
        *-isa
             description: ISA bridge
             product: 82801HEM (ICH8M) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-cdrom
                description: DVD-RAM writer
                product: DVDRW SSM-8515S
                vendor: Slimtype
                physical id: 0.0.0
                bus info: scsi@3:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: GSL1
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=open
        *-storage
             description: SATA controller
             product: 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0 module=ahci
           *-disk
                description: SCSI Disk
                product: FUJITSU MHW2160B
                vendor: ATA
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 0000
                serial: K102T75264CS
                size: 149GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: HPFS/NTFS partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 58GB
                   capabilities: primary bootable
              *-volume:1
                   description: Linux swap / Solaris partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   capacity: 4761MB
                   capabilities: primary nofs
              *-volume:2
                   description: Linux filesystem partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   capacity: 23GB
                   capabilities: primary
              *-volume:3
                   description: Linux filesystem partition
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   capacity: 62GB
                   capabilities: primary
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0

```


Whatever that tells you :confused:

---

### Post by Ulfursson on 2007-10-20
So, what now?

---

### Post by Ulfursson on 2007-10-20
Still sound-less here, with a 30gb library of mp3s gathering dust :guitar:

---

### Post by Pumalite on 2007-10-20
This is bad news:

 *-multimedia UNCLAIMED
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: latency=0

Multimedia UNCLAIMED ( I had to reinstall with this error, because to me it means the kernel is not loading the module) Check /home and see in 'Hidden Files' if you have an .asoundrc file.

---

### Post by Ulfursson on 2007-10-20
No, I don't have that file.

Couldn't I at least get it to detect my soundcard (it did detect it before, but refused to play sound) by undoing the edits I made to text config files as instructed on the alsa site?

---

### Post by Pumalite on 2007-10-20
You could try it. What do you have to loose?

---

### Post by Ulfursson on 2007-10-20
OK, I've re-installed Ubuntu. 
Let's give this another try:

How. Do. I. Get. My. Soundcard. Working?

---

### Post by Pumalite on 2007-10-20
If you reinstalled and still no sound, start checking your hardware.
Also beware of this:
[http://ubuntuforums.org/showthread.php?t=583007](http://ubuntuforums.org/showthread.php?t=583007)

---

### Post by Ulfursson on 2007-10-20
> **Pumalite said:**
> If you reinstalled and still no sound, start checking your hardware.
Also beware of this:
[http://ubuntuforums.org/showthread.php?t=583007](http://ubuntuforums.org/showthread.php?t=583007)

I'm pretty much back where I started - soundcard is detected properly (Intel HDA), but there is no sound.

---

### Post by Ulfursson on 2007-10-21
Help.
Please?

---

### Post by Ulfursson on 2007-10-21
Uh, this is slowly getting real frustrating. I've gotten pretty much everything else to work, sound is the only issue I've got left open.

---

### Post by nickless on 2007-10-21
Same Problem here by a pal of mine :neutral:
Would be very nice if a solution could be found... I was announcing ubuntu 7.10 for the past week everyday until it finally got him and he installed it. If this won't be solved he will switch back to Windows! :shock: Would be cool if we could make him stay with ubuntu 	[-o<

---

### Post by Ulfursson on 2007-10-21
Ah, someone else with a similar problem...it's good to see that I'm not alone.

---

### Post by pelle.k on 2007-10-21
Take it easy. You are not alone in this :)
Your soundcard is not supported with alsa 10.0.14 (shipped with ubuntu 7.10), so, the solution is to compile alsa (10.0.15) yourself.

Yeah, it's a pain in the ***, but this is the price you pay for new (very recent) technology. Check out the end of this thread (It'll tell you what to do);
[http://ubuntuforums.org/showpost.php?p=3588321&postcount=5](http://ubuntuforums.org/showpost.php?p=3588321&postcount=5)

---

### Post by Ulfursson on 2007-10-21
> **pelle.k said:**
> Take it easy. You are not alone in this :)
Your soundcard is not supported with alsa 10.0.14 (shipped with ubuntu 7.10), so, the solution is to compile alsa (10.0.15) yourself.

Yeah, it's a pain in the ***, but this is the price you pay for new (very recent) technology. Check out the end of this thread (It'll tell you what to do);
[http://ubuntuforums.org/showpost.php?p=3588321&postcount=5](http://ubuntuforums.org/showpost.php?p=3588321&postcount=5)

I've tried the metod described therein, but I got an error attempting to compile the driver:


```
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/bt87x.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/cmipci.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/cs4281.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/cs5530.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/ens1370.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/ens1371.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/es1938.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/es1968.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/fm801.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/intel8x0.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/intel8x0m.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/maestro3.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/rme32.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/rme96.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/sonicvibes.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/via82xx_modem.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/via82xx.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/snd-ad1889.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/snd-als300.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/snd-als4000.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/snd-atiixp.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/snd-atiixp-modem.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/snd-azt3328.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/snd-bt87x.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/snd-cmipci.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/snd-cs4281.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/snd-cs5530.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/snd-ens1370.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/snd-ens1371.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/snd-es1938.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/snd-es1968.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/snd-fm801.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/snd-intel8x0.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/snd-intel8x0m.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/snd-maestro3.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/snd-rme32.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/snd-rme96.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/snd-sonicvibes.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/snd-via82xx.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/snd-via82xx-modem.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/ac97/ac97_codec.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/ac97/ac97_pcm.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/ac97/ac97_proc.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/ac97/ak4531_codec.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/ac97/snd-ac97-codec.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/ac97/snd-ak4531-codec.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/ali5451/ali5451.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/ali5451/snd-ali5451.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/asihpi/asihpi.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/asihpi/hpimod.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/asihpi/hpidspcd.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/asihpi/hpios_linux_kernel.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/asihpi/snd-asihpi.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/au88x0/au8810.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/au88x0/au8820.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/au88x0/au8830.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/au88x0/snd-au8810.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/au88x0/snd-au8820.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/au88x0/snd-au8830.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/ca0106/ca0106_main.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/ca0106/ca0106_proc.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/ca0106/ca0106_mixer.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/ca0106/ca_midi.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/ca0106/snd-ca0106.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/cmi8788/cmi8788.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/cmi8788/cmi_lib.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/cmi8788/cmi_pcm.o
/home/eyjolf/alsa-driver-1.0.15/pci/cmi8788/cmi_pcm.c:579: warning: 'snd_cmi_pcm_ac97_playback_ops' defined but not used
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/cmi8788/cmi_mixer.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/cmi8788/patch_ak4396.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/cmi8788/patch_wm8785.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/cmi8788/patch_cmi9780.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/cmi8788/snd-cmi8788.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/cs46xx/cs46xx.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/cs46xx/cs46xx_lib.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/cs46xx/dsp_spos.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/cs46xx/dsp_spos_scb_lib.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/cs46xx/snd-cs46xx.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/cs5535audio/cs5535audio.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/cs5535audio/cs5535audio_pcm.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/cs5535audio/cs5535audio_pm.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/cs5535audio/snd-cs5535audio.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/echoaudio/darla20.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/echoaudio/darla24.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/echoaudio/echo3g.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/echoaudio/gina20.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/echoaudio/gina24.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/echoaudio/indigo.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/echoaudio/indigodj.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/echoaudio/indigoio.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/echoaudio/layla20.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/echoaudio/layla24.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/echoaudio/mia.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/echoaudio/mona.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/echoaudio/snd-darla20.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/echoaudio/snd-gina20.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/echoaudio/snd-layla20.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/echoaudio/snd-darla24.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/echoaudio/snd-gina24.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/echoaudio/snd-layla24.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/echoaudio/snd-mona.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/echoaudio/snd-mia.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/echoaudio/snd-echo3g.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/echoaudio/snd-indigo.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/echoaudio/snd-indigoio.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/echoaudio/snd-indigodj.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/emu10k1/emu10k1_synth.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/emu10k1/emu10k1_callback.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/emu10k1/emu10k1_patch.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/emu10k1/emu10k1.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/emu10k1/emu10k1_main.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/emu10k1/irq.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/emu10k1/memory.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/emu10k1/voice.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/emu10k1/emumpu401.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/emu10k1/emupcm.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/emu10k1/io.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/emu10k1/emuproc.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/emu10k1/emumixer.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/emu10k1/emufx.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/emu10k1/timer.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/emu10k1/p16v.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/emu10k1/emu10k1x.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/emu10k1/snd-emu10k1.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/emu10k1/snd-emu10k1-synth.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/emu10k1/snd-emu10k1x.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/hda/hda_intel.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/hda/hda_codec.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/hda/hda_proc.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/hda/hda_hwdep.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/hda/hda_generic.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/hda/patch_realtek.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/hda/patch_cmedia.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/hda/patch_analog.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/hda/patch_sigmatel.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/hda/patch_si3054.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/hda/patch_atihdmi.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/hda/patch_conexant.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/hda/patch_via.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/hda/snd-hda-intel.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/ice1712/ice1712.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/ice1712/delta.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/ice1712/hoontech.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/ice1712/ews.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/ice1712/ice1724.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/ice1712/amp.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/ice1712/revo.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/ice1712/aureon.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/ice1712/vt1720_mobo.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/ice1712/pontis.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/ice1712/prodigy192.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/ice1712/juli.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/ice1712/phase.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/ice1712/wtm.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/ice1712/ak4xxx.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/ice1712/snd-ice1712.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/ice1712/snd-ice17xx-ak4xxx.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/ice1712/snd-ice1724.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/korg1212/korg1212.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/korg1212/snd-korg1212.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/mixart/mixart.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/mixart/mixart_core.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/mixart/mixart_hwdep.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/mixart/mixart_mixer.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/mixart/snd-mixart.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/nm256/nm256.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/nm256/snd-nm256.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/pcxhr/pcxhr.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/pcxhr/pcxhr_hwdep.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/pcxhr/pcxhr_mixer.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/pcxhr/pcxhr_core.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/pcxhr/snd-pcxhr.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/pdplus/pdplus.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/pdplus/snd-pdplus.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/riptide/riptide.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/riptide/snd-riptide.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/rme9652/hdsp.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/rme9652/hdspm.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/rme9652/rme9652.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/rme9652/snd-rme9652.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/rme9652/snd-hdsp.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/rme9652/snd-hdspm.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/trident/trident_synth.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/trident/trident.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/trident/trident_main.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/trident/trident_memory.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/trident/snd-trident.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/trident/snd-trident-synth.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/vx222/vx222.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/vx222/vx222_ops.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/vx222/snd-vx222.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/ymfpci/ymfpci.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pci/ymfpci/ymfpci_main.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/ymfpci/snd-ymfpci.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pcmcia/pdaudiocf/pdaudiocf.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pcmcia/pdaudiocf/pdaudiocf_core.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pcmcia/pdaudiocf/pdaudiocf_irq.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pcmcia/pdaudiocf/pdaudiocf_pcm.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pcmcia/pdaudiocf/snd-pdaudiocf.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pcmcia/vx/vxpocket.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pcmcia/vx/vxp_ops.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/pcmcia/vx/vxp_mixer.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pcmcia/vx/snd-vxpocket.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/soc/soc-core.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/soc/soc-dapm.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/soc/snd-soc-core.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/synth/util_mem.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/synth/snd-util-mem.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/synth/emux/emux.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/synth/emux/emux_synth.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/synth/emux/emux_seq.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/synth/emux/emux_nrpn.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/synth/emux/emux_effect.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/synth/emux/emux_proc.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/synth/emux/emux_hwdep.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/synth/emux/soundfont.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/synth/emux/emux_oss.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/synth/emux/snd-emux-synth.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/usb/usbaudio.o
In file included from /home/eyjolf/alsa-driver-1.0.15/usb/usbaudio.c:2111:
/home/eyjolf/alsa-driver-1.0.15/alsa-kernel/usb/usbquirks.h:105:1: warning: "/*" within comment
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/usb/usbmixer.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/usb/usbmidi.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/usb/snd-usb-audio.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/usb/snd-usb-lib.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/usb/caiaq/caiaq-device.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/usb/caiaq/caiaq-audio.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/usb/caiaq/caiaq-midi.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/usb/caiaq/caiaq-input.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/usb/caiaq/snd-usb-caiaq.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/usb/usx2y/usbusx2y.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/usb/usx2y/usX2Yhwdep.o
  CC [M]  /home/eyjolf/alsa-driver-1.0.15/usb/usx2y/usx2yhwdeppcm.o
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/usb/usx2y/snd-usb-usx2y.o
  Building modules, stage 2.
  MODPOST 163 modules
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/acore/oss/snd-mixer-oss.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/acore/oss/snd-pcm-oss.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/acore/seq/instr/snd-ainstr-fm.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/acore/seq/instr/snd-ainstr-gf1.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/acore/seq/instr/snd-ainstr-iw.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/acore/seq/instr/snd-ainstr-simple.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/acore/seq/oss/snd-seq-oss.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/acore/seq/snd-seq-device.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/acore/seq/snd-seq-dummy.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/acore/seq/snd-seq-instr.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/acore/seq/snd-seq-midi-emul.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/acore/seq/snd-seq-midi-event.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/acore/seq/snd-seq-midi.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/acore/seq/snd-seq-virmidi.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/acore/seq/snd-seq.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/acore/snd-hwdep.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/acore/snd-page-alloc.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/acore/snd-pcm.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/acore/snd-rawmidi.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/acore/snd-rtctimer.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/acore/snd-timer.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/acore/snd.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/drivers/mpu401/snd-mpu401-uart.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/drivers/mpu401/snd-mpu401.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/drivers/opl3/snd-opl3-lib.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/drivers/opl3/snd-opl3-synth.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/drivers/opl4/snd-opl4-lib.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/drivers/opl4/snd-opl4-synth.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/drivers/pcsp/snd-pcsp.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/drivers/snd-aloop.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/drivers/snd-dummy.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/drivers/snd-mtpav.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/drivers/snd-mts64.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/drivers/snd-portman2x4.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/drivers/snd-serial-u16550.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/drivers/snd-virmidi.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/drivers/vx/snd-vx-lib.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/i2c/other/snd-ak4114.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/i2c/other/snd-ak4117.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/i2c/other/snd-ak4xxx-adda.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/i2c/other/snd-pt2258.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/i2c/other/snd-tea575x-tuner.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/i2c/snd-cs8427.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/i2c/snd-i2c.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/i2c/snd-tea6330t.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/isa/ad1816a/snd-ad1816a.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/isa/ad1848/snd-ad1848-lib.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/isa/ad1848/snd-ad1848.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/isa/cs423x/snd-cs4231-lib.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/isa/cs423x/snd-cs4231.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/isa/cs423x/snd-cs4232.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/isa/cs423x/snd-cs4236-lib.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/isa/cs423x/snd-cs4236.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/isa/es1688/snd-es1688-lib.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/isa/es1688/snd-es1688.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/isa/gus/snd-gus-lib.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/isa/gus/snd-gus-synth.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/isa/gus/snd-gusclassic.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/isa/gus/snd-gusextreme.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/isa/gus/snd-gusmax.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/isa/gus/snd-interwave-stb.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/isa/gus/snd-interwave.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/isa/msnd/snd-msnd-pinnacle.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/isa/opti9xx/snd-miro.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/isa/opti9xx/snd-opti92x-ad1848.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/isa/opti9xx/snd-opti92x-cs4231.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/isa/opti9xx/snd-opti93x.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/isa/sb/snd-emu8000-synth.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/isa/sb/snd-es968.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/isa/sb/snd-sb-common.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/isa/sb/snd-sb16-csp.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/isa/sb/snd-sb16-dsp.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/isa/sb/snd-sb16.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/isa/sb/snd-sb8-dsp.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/isa/sb/snd-sb8.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/isa/sb/snd-sbawe.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/isa/snd-adlib.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/isa/snd-als100.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/isa/snd-azt2320.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/isa/snd-cmi8330.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/isa/snd-dt019x.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/isa/snd-es18xx.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/isa/snd-opl3sa2.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/isa/snd-sc6000.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/isa/snd-sgalaxy.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/isa/snd-sscape.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/isa/wavefront/snd-wavefront.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/misc/ac97_bus.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/ac97/snd-ac97-codec.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/ac97/snd-ak4531-codec.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/ali5451/snd-ali5451.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/asihpi/snd-asihpi.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/au88x0/snd-au8810.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/au88x0/snd-au8820.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/au88x0/snd-au8830.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/ca0106/snd-ca0106.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/cmi8788/snd-cmi8788.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/cs46xx/snd-cs46xx.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/cs5535audio/snd-cs5535audio.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/echoaudio/snd-darla20.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/echoaudio/snd-darla24.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/echoaudio/snd-echo3g.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/echoaudio/snd-gina20.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/echoaudio/snd-gina24.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/echoaudio/snd-indigo.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/echoaudio/snd-indigodj.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/echoaudio/snd-indigoio.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/echoaudio/snd-layla20.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/echoaudio/snd-layla24.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/echoaudio/snd-mia.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/echoaudio/snd-mona.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/emu10k1/snd-emu10k1-synth.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/emu10k1/snd-emu10k1.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/emu10k1/snd-emu10k1x.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/hda/snd-hda-intel.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/ice1712/snd-ice1712.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/ice1712/snd-ice1724.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/ice1712/snd-ice17xx-ak4xxx.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/korg1212/snd-korg1212.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/mixart/snd-mixart.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/nm256/snd-nm256.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/pcxhr/snd-pcxhr.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/pdplus/snd-pdplus.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/riptide/snd-riptide.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/rme9652/snd-hdsp.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/rme9652/snd-hdspm.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/rme9652/snd-rme9652.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/snd-ad1889.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/snd-als300.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/snd-als4000.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/snd-atiixp-modem.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/snd-atiixp.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/snd-azt3328.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/snd-bt87x.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/snd-cmipci.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/snd-cs4281.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/snd-cs5530.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/snd-ens1370.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/snd-ens1371.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/snd-es1938.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/snd-es1968.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/snd-fm801.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/snd-intel8x0.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/snd-intel8x0m.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/snd-maestro3.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/snd-rme32.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/snd-rme96.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/snd-sonicvibes.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/snd-via82xx-modem.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/snd-via82xx.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/trident/snd-trident-synth.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/trident/snd-trident.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/vx222/snd-vx222.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pci/ymfpci/snd-ymfpci.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pcmcia/pdaudiocf/snd-pdaudiocf.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/pcmcia/vx/snd-vxpocket.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/soc/snd-soc-core.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/synth/emux/snd-emux-synth.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/synth/snd-util-mem.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/usb/caiaq/snd-usb-caiaq.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/usb/snd-usb-audio.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/usb/snd-usb-lib.ko
  LD [M]  /home/eyjolf/alsa-driver-1.0.15/usb/usx2y/snd-usb-usx2y.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
utils/link-modules /home/eyjolf/alsa-driver-1.0.15

ALSA modules were successfully compiled.

if [ -L /usr/include/sound ]; then \
                rm -f /usr/include/sound; \
                ln -sf /home/eyjolf/alsa-driver-1.0.15/include/sound /usr/include/sound; \
        else \
                rm -rf /usr/include/sound; \
                install -d -m 755 -g root -o root /usr/include/sound; \
                for f in include/sound/*.h; do \
                        install -m 644 -g root -o root $f /usr/include/sound; \
                done \
        fi
install: cannot create directory `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
make: *** [install-headers] Error 1
eyjolf@ANDLANG:~/alsa-driver-1.0.15$ 
```

I don't understand why this happened, I did run it in sudo mode.

---

### Post by pelle.k on 2007-10-21
Listen, you can't run
```
sudo ./configure; make; make install
```
that is essentially three (3) commands, where only the first has sudo privilegies.

"make install" *has* to be run with sudo. :)

---

### Post by Ulfursson on 2007-10-21
> **pelle.k said:**
> Listen, you can't run
```
sudo ./configure; make; make install
```
that is essentially three (3) commands, where only the first has sudo privilegies.

"make install" *has* to be run with sudo. :)

That would explain it, I guess.

Anyway, I currently don't have access to my laptop (at work), so I'll post results later.

---

### Post by basbeek on 2007-10-24
Hello Ulfursson,

I had the same sound problems that you are having... (same laptop)..

anyway after some googling I foud this link with which I as able to get my sound to work.

[http://lddubeau.com/avaktavyam/linux-on-a-compal-ifl90/]("http://lddubeau.com/avaktavyam/linux-on-a-compal-ifl90/")

The steps are easy to follow.

Hope this helps you,

Bas

---

### Post by VCSkier on 2008-03-08
I have no idea how I came across this thread, or if you have found your solution, but my wife's laptop had the same problem, with the same sound device.  I came across [this advice]("http://ubuntuforums.org/showpost.php?p=884287&postcount=6"), and fixed the problem.  This is actually his advice slightly cleaned up.

[LIST=1]
[*]Right-Click on the speaker icon in your top panel
[*]Select "Open Volume Control"
[*]Select "Edit"->"Preferences"
[*]Near the bottom of the new window, check "External Amplifier" so you can control that switch
[*]Go to the "Switches" tab, and turn off "External Amplifier"
[/LIST]

On my wife's laptop that fixed it.  I had tried compiling drivers and all sorts of other fixes like you have, and all they did was cause more problems.  So finally I did a fresh install and tried this simple fix, and we haven't had any problems sense.  Don't give up.  You really will be so much happier with Ubuntu, or any other Free OS than with anything non-Free, once you get things running.

---

### Post by pelle.k on 2008-03-10
Just as a remainder that the backport repositories contain updated alsa modules (among other things).
The actual package is named "linux-backports-modules".

---

### Post by Teeb0 on 2008-03-24
I have the same computer (IFL90), and I have the same problem with sound in Ubuntu gutsy 64-bit. I have tried the [ALSA-thing]("http://lddubeau.com/avaktavyam/linux-on-a-compal-ifl90/") (1.0.15rc3), but then ubuntu could no longer identify my sound card. I have seen people with the same machine fixing their problem with the method mentioned.

I have a theory that these ppl use ubuntu 32-bit, and not 64-bit, like I do. That's it, isn't it?

---

### Post by pelle.k on 2008-03-24
linux-backports-modules has got alsa 1.0.15 (release), so try installing that after activating the backports repositories in synaptic (or sources.list if you're a command line guy).
If it still can't identify your sound card, then;
1. does it load the module? (use "lsmod | grep snd-hda-intel" to check). If so, comment out every line about that module in /etc/modprobe.d/alsa-base and try "option snd-hda-intel model=toshiba" in there instead.
2. if it doesn't load the module automatically, put "snd-hda-intel" in /etc/modules

---

### Post by knobcottage on 2008-04-05
The first url fixes the sound and the second fixes the compiz.  Worked a treat on mine.  Just came up with something saying mplayer.conf did not exist.

[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

Compal IFL 91
          o Codec: Realtek ALC268
          o Works with Alsa 1.0.15:
          o Add following line to /etc/modprobe.d/alsa-base and reboot.
          o options snd-hda-intel index=0 model=toshiba

[https://wiki.ubuntu.com/LaptopTestingTeam/CompalIFL91?highlight=%28fl91%29](https://wiki.ubuntu.com/LaptopTestingTeam/CompalIFL91?highlight=%28fl91%29)

    *Sound card needs Alsa-base version 1.0.15 or newer (Gutsy default 1.0.14)
    *Mic capture volume needs to be turned up to hear what you record?: sudo amixer set Capture 90 cap
    *In Gutsy the Intel video card is blacklisted in Compiz, because the XV video mode does not work. Can be fixed by removing the blacklisting and using   	some other video mode, like X11 (but might be slower?)

sudo perl -pi -e 's|T="\$T 8086:2982|#T="\$T 8086:2982|' /usr/bin/compiz

# asetus ei ole pysyvä, compiz-päivitys kirjoittaa sen yli
# pysyväksi sen saisi esim lisäämällä /etc/skel-hakemistoon compiz-skriptin, joka on oletuksena päällä
# sudo cp -r compiz /etc/skel/.config/
# ..tällöin jokaisen käyttäjän kotihakemistossa olisi asetus, mikä ohittaa tarkistukset
# ks. compiz-hakemiston sisältö ja ohje-työpöytätehosteet.txt

# aktivoi toimiva oikea videotila
sudo gconftool-2 --direct \
  --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults \
  --type string \
  --set /system/gstreamer/0.10/default/videosink ximagesink
 
sudo perl -pi -e 's|vo=xv|vo=x11|' /etc/mplayer/mplayer.conf

---

### Post by unimatrix on 2008-05-18
I had the same problem on Compal FL90 in Ubuntu 7.10
All I had to do was install linux-backports-modules and it worked.

On Ubuntu 8.04 it worked out of the box.

---

