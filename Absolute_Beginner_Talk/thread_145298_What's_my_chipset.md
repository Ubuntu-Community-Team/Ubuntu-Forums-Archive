---
title: "What's my chipset"
date: 2006-03-16
forum: Absolute Beginner Talk
---

### Post by don cole on 2006-03-16
Hi,

The first instruction says identify your chipset.

What's my chipset identification?

Here's my scanModem report:

----------------------------------


 DO use the following line as the email Subject Line, to alert cogent experts:
      scanModem, Ubuntu 5.10 "Breezy Badger"  kernel 2.6.12-9-386  
 Occassionally reponses are blocked by an Internet Provider mail filters.
 So do in a day also check the Archived responses at [email]DISCUSS@linmodems.org[/email]
Code updated on:  2006_March_07
------------ --------------  System information ------------------------
 Ubuntu 5.10 "Breezy Badger" 
 on System with processor: i686
 currently under kernel:   2.6.12-9-386
 [https://wiki.ubuntu.com/DialupModemHowto](https://wiki.ubuntu.com/DialupModemHowto) has good general guidance.
A /dev/modem symbolic link is not present
 USB modem not detected.

 Checking for audio card 
0000:00:0c.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 04)
	Reading /proc/asound/pcm 
00-00: emu10k1 : ADC Capture/Standard PCM Playback : playback 32 : capture 1
00-01: emu10k1 mic : Mic Capture : capture 1
00-02: emu10k1 efx : Multichannel Capture/PT Playback : playback 8 : capture 1
00-03: emu10k1 : Multichannel Playback : playback 1


 The kernel was assembled with compiler:  3.4.5
 a gcc-3.4.5  package must be installed to support driver compiling
To support compiling, get the  BreezyGCC_3.4_i386.tar.gz from [http://phep2.technion.ac.il/linmodems/packages/smartlink/](http://phep2.technion.ac.il/linmodems/packages/smartlink/) 

 Compiling utility   make   Not found.

Checking for kernel-headers needed for compiling.
 Kernel-header resources needed for compiling are not manifestly ready!

Modem candidates are at PCI_buses:  0000:00:09.0
    
Providing detail for device at  0000:00:09.0
  with vendor-ID:device-ID
	    ----:----
Class 0703: 2000:2800   Modem: Smart Link Ltd.: Unknown device 2800 (rev 02) (prog-if 00 [Generic])
  SubSystem 122d:2800  Aztech System Ltd: Unknown device 2800
	Flags: medium devsel, IRQ 5
 Checking for IRQ 5 sharing with modem.
      XT-PIC  uhci_hcd:usb1
      XT-PIC  ide1

  
                  -----PCI_IDs-------                    --CompilerVer- 
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 2000:2800 122d:2800 debian_version 2.6.12-9-386  3.4.5 none    i686

The SmartLink slamr driver supports this modem:
    2000:2800  Gateway SL2800
complemented by the SmartLink slmodemd.

 == Checking PCI IDs through modem chip suppliers ==

 SmartLink at [http://www.smlink.com/](http://www.smlink.com/) owns vendor IDs 163c, 2000, 2003, and 2004
 The official download site is:  [http://www.smlink.com/main/index1.php?ln=en&main_id=40](http://www.smlink.com/main/index1.php?ln=en&main_id=40)
 But a more recent code and a much broader license for other chipset support,
 can be downloaded from [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/)  
 Though not always needed, download the files: 
   slmodem-CurrentVersion.tar.gz - provides the most general code package.
   SLMODEMD.gcc3 - provides a compiled slmodemd 
   ungrab-winmodem.tar.gz  -  may be needed for usage with slamr. 
 Details on their usage are in Slmodem.txt, Slmodem-ALSA.txt and
 [http://linmodems.technion.ac.il/slmodem-serial.html](http://linmodems.technion.ac.il/slmodem-serial.html)


  ======= PCI_ID checking completed ====== 
 Update=2006_March_07
A PCMCIA CardBus is not detected on this System.
drwxr-xr-x  2 root root 0 2006-03-12 01:16 /dev/.udevdb

There is an active UDEV file system, creating device nodes in volatile RAM.
For SmartLink modems using the slamr.ko or slusb.ko drivers an /etc/init.d/ script
will be necessary to create /dev/slamr0 or /dev/slusb0 ports, or manually by:
#  mknod -m 600 /dev/slamr0 c 242 0
#  mknod -m 600 /dev/slusb0 c 243 0
upon each bootup.

For information on modem port creation under the UDEV device file system see:
   [http://linmodems.technion.ac.il/archive-fourth/msg03299.html](http://linmodems.technion.ac.il/archive-fourth/msg03299.html)  for Conexnant modems
   [http://linmodems.technion.ac.il/archive-fifth/msg01177.html](http://linmodems.technion.ac.il/archive-fifth/msg01177.html)  for Lucent/Agere DSP modems
   
 Checking for modem symbolic link support lines within /etc/udev/ files


Checking the /etc/apt/sources.list
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted



deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse




deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe main restricted multiverse

A package kernel-kbuild-2.6-3 or later version must be installed to support compiling


      
 The Major.Minor versions differ in the designated compiler none and the 3.4.5 used in kernel assembly!!"
But there must be a match on the target for driver installation, 
of gcc Major.Minor versions or kernel and drivers!!
Otherwise the drivers will fail to load with warning:
  Invalid module format!!"
See [http://linmodems.technion.ac.il/archive-fifth/msg04252.html](http://linmodems.technion.ac.il/archive-fifth/msg04252.html) 
 
Kernel-header resources needed for compiling are not manifestly ready!
Checking /usr/src/ for compressed compressed headers or kernel-source

Kernel-header resources needed for compiling are not manifestly ready!
If compressed resources are present, expand and then configure them following DriverCompiling.txt
They may have to be installed.
Within your Linux distributions' installation CD or online resource (and mirrows), search for :
  Distribution  PackageName			OnLine
  ----------------------------------------------------------------------
 Debian  		kernel-headers-2.6.12-9-386    	[http://www.debian.org/distrib/packages](http://www.debian.org/distrib/packages) or install CD
 Ubuntu 		linux-headers-2.6.12-9-386		[http://http://packages.ubuntu.com/](http://http://packages.ubuntu.com/) or install CD
 Xandros
                        kernel-kbuild-3.6 are additionally required by  Debian, Ubuntu and Xandros
 Mandrake 	kernel-source-2.6.12-9-386	   If not present on install CDs search
 	[http://mirror.switch.ch/ftp/mirror/mandrake/official/10.0/i586/Mandrake/RPMS/](http://mirror.switch.ch/ftp/mirror/mandrake/official/10.0/i586/Mandrake/RPMS/) 
	[http://rpms.mandrakeclub.com/rpms/mandrake/official/LByName.html](http://rpms.mandrakeclub.com/rpms/mandrake/official/LByName.html), or other mirrors.
  SuSE		kernel-source-2.6.12-9-386		 , kernels are named k_deflt
  FedoraCore4  kernel-devel-2.6.12-9-386 or kernel-smp-devel-2.6.12-9-386 on install CD1 or CD4
One of which must be installed if compiling drivers to match kernel 2.6.12-9-386 proves necessary.
Within the output Modem/ folder, read CompilingDrivers.txt for details.
   

 A /dev/modem symbolic link is not set.

The following information blocks just query some ppp support items.

====================================================
   grep -rs ppp /etc/modprobe.*
-------------------------------------
/etc/modprobe.d/aliases:alias net-pf-24 pppoe
/etc/modprobe.d/aliases:alias ppp-compress-18 ppp_mppe_mppc
-------------------------------------
 Resident PPP support modules are properly uncompressed .
 COMM services are not active
Be sure to read the section about ppp related modules and aliases in Modem/YourSystem.txt
 ---- dmesg queries -------
[4294667.296000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[4294669.407000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[4294669.463000] audit: initializing netlink socket (disabled)
[4294669.921000] ACPI: PCI interrupt for device 0000:00:09.0 disabled
[4294717.607000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4294717.607000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294730.906000] ibm_acpi: ec object not found
[4294747.456000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294747.456000] apm: overridden by ACPI.

  pppd version 2.4.2 may not be fully compatible with 2.6.8 kernel releases.
  If an initial CONNECT is achieved without PPP being subsequently established,
  drop back to a 2.4.1 version.  This has worked for PCTEL AMR modem users,
  supported by the [http://www.smlink.com](http://www.smlink.com)  slmodem software.
  Check pppd version with:
    pppd --version
  See  [http://linmodems.technion.ac.il/archive-fourth/msg03167.html](http://linmodems.technion.ac.il/archive-fourth/msg03167.html)
    
  debian_version is not yet providing pre-compiled drivers for WinModems

--------------------------------------------------
Thank you ,
Don Cole

---

### Post by chimera on 2006-03-16
do

```

sudo lshw

```

and post the output here

---

### Post by don cole on 2006-03-16
Thank you,

don@ubuntu:~$ sudo lshw
Password:
ubuntu
    description: Tower Computer
    product: System Name
    vendor: System Manufacturer
    version: System Version
    serial: SYS-1234567890
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=tower
  *-core
       description: Motherboard
       product: <P3B-F>
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: REV 1.xx
       serial: xxxxxxxxxxx
       slot: SECONDARY IDE/HDD
     *-firmware
          description: BIOS
          vendor: Award Software, Inc.
          physical id: 0
          version: ASUS P3B-F ACPI BIOS Revision 1007 Beta 001 (07/26/2000)
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
          size: 500MHz
          capacity: 800MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse
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
          size: 160MB
          capacity: 1GB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: DIMM 1
             size: 64MB
             width: 64 bits
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: DIMM 2
             size: 64MB
             width: 64 bits
        *-bank:2
             description: DIMM DRAM Synchronous
             physical id: 2
             slot: DIMM 3
             size: 32MB
             width: 64 bits
        *-bank:3
             description: DIMM DRAM Synchronous [empty]
             physical id: 3
             slot: DIMM 4
     *-pci
          description: Host bridge
          product: 440BX/ZX/DX - 82443BX/ZX/DX Host bridge
          vendor: Intel Corporation
          physical id: e4000000
          bus info: pci@00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
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
                product: 3D Rage Pro AGP 1X/2X
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@01:00.0
                version: 5c
                size: 16MB
                width: 32 bits
                clock: 33MHz
                capabilities: vga bus_master cap_list
                resources: iomemory:e3000000-e3ffffff ioport:d800-d8ff iomemory:e0800000-e0800fff irq:11
        *-isa UNCLAIMED
             description: ISA bridge
             product: 82371AB/EB/MB PIIX4 ISA
             vendor: Intel Corporation
             physical id: 4
             bus info: pci@00:04.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
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
             configuration: driver=PIIX_IDE
             resources: ioport:b800-b80f
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk:0
                   description: ATA Disk
                   product: QUANTUM BIGFOOT TS19.2A
                   vendor: Quantum
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: A21.0G00
                   serial: 382906880706
                   size: 17GB
                   capacity: 17GB
                   capabilities: ata dma lba iordy smart pm
                   configuration: mode=udma2 smart=on
              *-disk:1
                   description: ATA Disk
                   product: WDC AC22100H
                   vendor: Western Digital
                   physical id: 1
                   bus info: ide@0.1
                   logical name: /dev/hdb
                   version: 10.07H09
                   serial: WD-WT3610207927
                   size: 2014MB
                   capacity: 2014MB
                   capabilities: ata dma lba iordy
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: WDC WD64AA
                   vendor: Western Digital
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: 80.10A80
                   serial: WD-WM6530448615
                   size: 6149MB
                   capacity: 6149MB
                   capabilities: ata dma lba iordy smart pm
                   configuration: mode=udma2 smart=on
              *-cdrom
                   description: IDE CD-ROM
                   product: NEC CD-ROM DRIVE:28B
                   physical id: 1
                   bus info: ide@1.1
                   logical name: /dev/hdd
                   version: 3.05
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio
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
             configuration: driver=uhci_hcd
             resources: ioport:b400-b41f irq:5
           *-usbhost
                product: Intel Corporation 82371AB/EB/MB PIIX4 USB
                vendor: Linux 2.6.12-9-386 uhci_hcd
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
             configuration: driver=piix4_smbus
             resources: irq:9
        *-communication UNCLAIMED
             description: Modem
             product: Smart Link Ltd.
             vendor: Smart Link Ltd.
             physical id: 9
             bus info: pci@00:09.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: generic cap_list
             resources: iomemory:e1000000-e1ffffff irq:5
        *-network DISABLED
             description: Ethernet interface
             product: RTL8139 Ethernet
             vendor: D-Link System Inc
             physical id: a
             bus info: pci@00:0a.0
             logical name: eth0
             version: 10
             serial: 00:40:05:7c:84:ac
             size: 10MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
             configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=half link=no multicast=yes port=MII speed=10MB/s
             resources: ioport:b000-b0ff iomemory:e0000000-e00000ff irq:10
        *-multimedia
             description: Multimedia audio controller
             product: SB Live! EMU10k1
             vendor: Creative Labs
             physical id: c
             bus info: pci@00:0c.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=EMU10K1_Audigy
             resources: ioport:a800-a81f irq:11
        *-input
             description: Input device controller
             product: SB Live! MIDI/Game Port
             vendor: Creative Labs
             physical id: c.1
             bus info: pci@00:0c.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Emu10k1_gameport
             resources: ioport:a400-a407

---

### Post by StefanoCole on 2006-03-16
With the command: 

sudo lshw 

you get the chipset of your motherboard, not the chipset of your modem. You have to find your modem chipset in the ModemData.txt file which is the output of scanModem utility.

Stefano

---

### Post by don cole on 2006-03-17
I know that but where is the line that shows that info?

Don Cole

---

### Post by chimera on 2006-03-17
> description: Motherboard
product: <P3B-F>
vendor: ASUSTeK Computer INC.


According to [google](http://www.google.com/search?q=asus+p3f+b&start=0&start=0&ie=utf-8&oe=utf-8&client=firefox&rls=org.mozilla:en-US:unofficial) , that motherboard has the 440BX chipset.

---

### Post by klahjn on 2006-03-17
nice.....the 440bx chipset from the research i've seen so far has been "the best chipset" for stability and performance.  From the information that i've gathered it usually takes a hammer or a glass of water to stop a 440bx from working.  Don't trade that puppy in for anything, just buy a new machine when you need to upgrade and use that as a fileserver or something when the time arises.

---

### Post by StefanoCole on 2006-03-17
Don Cole, in the file ModemData.txt the lines related to your modem are: > Modem candidates are at PCI_buses: 0000:00:09.0

Providing detail for device at 0000:00:09.0
with vendor-ID:device-ID
----:----
Class 0703: 2000:2800 Modem: Smart Link Ltd.: Unknown device 2800 (rev 02) (prog-if 00 [Generic])
SubSystem 122d:2800 Aztech System Ltd: Unknown device 2800

It seems that the vendor of your modem is Smart Link but it also seems that the scanModem utility is not able to detect the related chipset (Unknown device 2800)

Stefano

---

