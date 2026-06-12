---
title: "Toshiba A100 - Teething problems!"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by benpage26 on 2008-02-14
Hello I have installed the latest Ubuntu on my laptop recently.  I know that laptops are not meant to work very well on Ubuntu, but if i can work out how to fix mine then maybe the next person who installs Ubuntu on an A100 will get it working out of the box, isn't that the point of open-source. :) or maybe someone has already got the stuff fixed and i just need to apply the fixes.

Sorry if this seems a little rude, but I am going to list all the things that are not working, and ask you people very nicely to direct me to where or how i could fix them.   Pwwese?

[LIST]
[*]Card reader (inbuilt)
[*]Multimedia Buttons on keyboard
[*]Graphics (selecting TV-OUT/VGA-OUT don't work)
[*]Power control (toshiba had a windows util that let me cycle through high, low, med power modes and stuff)
[*]Fan speed/CPU settings - my laptop runs really hot :( i really want to fix that
[*]Screen brightness
[*]All the Fn+FKEY buttons do not work
[*]Standby never works
[/LIST]

Hopefully you can help me.  Ben

---

### Post by Origin415 on 2008-02-14
You could try looking here: [http://www.linux-on-laptops.com/toshiba.html](http://www.linux-on-laptops.com/toshiba.html)

---

### Post by benpage26 on 2008-02-14
There is no info on my Toshiba A100 :(
There are similar laptops of a similar spec but the pages just say that those installs worked out of the box.

Could it be i will not get all the issues on the LTS version?
Is there anyway i can install the two side by side?

---

### Post by xeth_delta on 2008-02-14
> **benpage26 said:**
> Hello I have installed the latest Ubuntu on my laptop recently.  I know that laptops are not meant to work very well on Ubuntu, but if i can work out how to fix mine then maybe the next person who installs Ubuntu on an A100 will get it working out of the box, isn't that the point of open-source. :) or maybe someone has already got the stuff fixed and i just need to apply the fixes.

Sorry if this seems a little rude, but I am going to list all the things that are not working, and ask you people very nicely to direct me to where or how i could fix them.   Pwwese?

[LIST]
[*]Card reader (inbuilt)
[*]Multimedia Buttons on keyboard
[*]Graphics (selecting TV-OUT/VGA-OUT don't work)
[*]Power control (toshiba had a windows util that let me cycle through high, low, med power modes and stuff)
[*]Fan speed/CPU settings - my laptop runs really hot :( i really want to fix that
[*]Screen brightness
[*]All the Fn+FKEY buttons do not work
[*]Standby never works
[/LIST]

Hopefully you can help me.  Ben

Welcome to the forums! Right now it;s kind of late where I leave, so I will post more tomorrow. For now, some sketchy information:
Card reader:
Whether ot not the card will work depends on the specifications the developers had available. Sometimes certain producer chooses not to release much information, something that makes the work of FOSS programmers much more difficult.

It would help if you post the outpuy of the following commands (please paste between CODE tags):
```
lspci
lsusb
sudo lshw
```

Multimedia buttons:
Open a terminal and type "xev". A small window will open. Try the buttons and check if there is any output in the original terminal.

Graphics (selecting TV-OUT/VGA-OUT don't work):
You might need to make some changes to the file "/etc/X11.xorg.conf". Can you please post its contents?

Power control (cycle through high, low, med power modes and stuff):
There is such an option, at least in the Desktop environment I use, KDE. Maybe some Gnome users can offer some help on that. Search through the forums, there must be some discussions on this.

Fan speed/CPU settings - my laptop runs really hot:
You can actually control the speed of the fan manually, if you want (not recommened), set a minimum speed, etc. I can write more on this tomorrow, meanwhile issue a search in the forums, I've seen some threads on exactly this.

What is the CPU temperature, btw?

Screen brightness:
Can be changed, if not from the keyboard, most likely via software, but more information on the hardware is needed.

All the Fn+FKEY buttons do not work
I am not sure what to say here, maybechoosing a different layout. Test again with xev.

Standby never works:
This can be a problem with certain laptops. A frequent cause is one of the modules (drivers) not recovering after standby. You can try to identify it by starting a safe mode / pure command line session, unload modules and try putting the system in standby.

To see what modules are loaded:
```
lsmod
```
to unload
```
sudo rmmod module_name
```

Please backup any important information before.

What version of Ubuntu are you using.

Let us know if you need any extra help. :)

---

### Post by benpage26 on 2008-02-14
> **xeth_delta said:**
> 
It would help if you post the outpuy of the following commands (please paste between CODE tags):
lspci command
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
07:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
07:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
07:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
07:06.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
07:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
ben@winegums:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
07:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
07:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
07:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
07:06.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
07:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)

```
lsusb command
```
ben@winegums:~$ lsusb
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  

```
sudo lshw command
```
ben@winegums:~$ sudo lshw
winegums                  
    description: Computer
    product: EQUIUM A100
    vendor: TOSHIBA
    version: PSAABE-00800EAV
    serial: X6465199Q
    width: 32 bits
    capabilities: smbios-2.31 dmi-2.31
    configuration: administrator_password=enabled boot=oem-specific frontpanel_password=unknown keyboard_password=unknown power-on_password=enabled uuid=566B4600-6425-11DB-A70E-00A0D15B2B47
  *-core
       description: Motherboard
       product: MPAD-MSAE Customer Reference Boards
       vendor: Intel Corporation
       physical id: 0
       version: Not Applicable
       serial: Not Applicable
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: 2.00 (08/30/2006)
          size: 111KB
          capacity: 960KB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd cdboot acpi usb agp biosbootspecification
     *-cpu
          description: CPU
          product: Genuine Intel(R) CPU           T2050  @ 1.60GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.14.8
          serial: 0000-06E8-0000-0000-0000-0000
          slot: U1
          size: 1600MHz
          capacity: 1600MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pni monitor est tm2 xtpr cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 16KB
             capacity: 16KB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 2MB
             capabilities: burst external write-back
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 12
          slot: System board or motherboard
          size: 1GB
          capacity: 2GB
        *-bank:0
             description: SODIMM DDR Synchronous
             physical id: 0
             slot: M1
             size: 512MB
             width: 32 bits
        *-bank:1
             description: SODIMM DDR Synchronous
             physical id: 1
             slot: M2
             size: 512MB
             width: 32 bits
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display:0
             description: VGA compatible controller
             product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm vga bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:0
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Network controller
                product: PRO/Wireless 3945ABG Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:05:00.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=ipw3945 latency=0 module=ipw3945
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-pcmcia
                description: CardBus bridge
                product: PCIxx12 Cardbus Controller
                vendor: Texas Instruments
                physical id: 6
                bus info: pci@0000:07:06.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
           *-firewire
                description: FireWire (IEEE 1394)
                product: PCIxx12 OHCI Compliant IEEE 1394 Host Controller
                vendor: Texas Instruments
                physical id: 6.1
                bus info: pci@0000:07:06.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=ohci1394 latency=128 maxlatency=4 mingnt=2 module=ohci1394
           *-storage
                description: Mass storage controller
                product: 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
                vendor: Texas Instruments
                physical id: 6.2
                bus info: pci@0000:07:06.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm bus_master cap_list
                configuration: driver=tifm_7xx1 latency=128 maxlatency=4 mingnt=7 module=tifm_7xx1
           *-system
                description: Generic system peripheral
                product: PCIxx12 SDA Standard Compliant SD Host Controller
                vendor: Texas Instruments
                physical id: 6.3
                bus info: pci@0000:07:06.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci latency=128 maxlatency=4 mingnt=7 module=sdhci
           *-network
                description: Ethernet interface
                product: PRO/100 VE Network Connection
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:07:08.0
                logical name: eth0
                version: 02
                serial: 00:a0:d1:5b:2b:47
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI duplex=full firmware=N/A ip=192.168.1.100 latency=66 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801GBM/GHM (ICH7 Family) SATA IDE Controller
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
                product: FUJITSU MHV2060B
                vendor: ATA
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 0000
                serial: NW9AT692F9PB
                size: 55GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: Linux filesystem partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 53GB
                   capabilities: primary bootable
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 2384MB
                   capacity: 2384MB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2384MB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: DVD-RW  DVR-K16A
                vendor: PIONEER
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.63
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=open
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0

```
> **xeth_delta said:**
> 
Multimedia buttons:
Open a terminal and type "xev". A small window will open. Try the buttons and check if there is any output in the original terminal.
There was no output in the window when i pressed the multimedia keys



> **xeth_delta said:**
> 
Graphics (selecting TV-OUT/VGA-OUT don't work):
You might need to make some changes to the file "/etc/X11.xorg.conf". Can you please post its contents?
```
ben@winegums:/etc/X11$ cat xorg.conf 
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "gb"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizEdgeScroll"       "0"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
        Driver          "intel"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1280x800"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

# Uncomment if you have a wacom tablet
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

```

> **xeth_delta said:**
> What is the CPU temperature, btw?
I don't know the sensor readings, but i can feel it get very hot on the part where my wrists rest as I type :o :(

About the screen brightness, I have used the Brightness Applet that you can add to a GNOME panel, as well as trying to use the KB shortcuts that used to work on WinXP, neither have worked.

Your suggestion for standby, if i was in a console only mode i wouldn't know how to put it in standby.  (I can probably look that up though).  And are you suggesting trying the standby over and over again with different modules unloaded until it works?


Thanks for your help

---

### Post by pt_lam on 2008-04-14
Similar problem here. My major worry is the temperature.
Can anyone help?
Thanks!

---

### Post by benpage26 on 2008-04-14
Hi pt_lam,

Since i posted this I have been trying to sort out the heat problems.  For now I have given up.  I just keep an eye and shut down the laptop whenever it gets too hot.  Shame really.

---

### Post by OldTimeTech on 2008-04-14
Check in Synaptic Package Manager....in search type laptop, comes up with a number of programs to help there is one program called Ktemperature that might help with the heat and even though it's a kde program should also work in gnome.

P.S. also has a Toshiba laptop utilities.

---

### Post by Inxsible on 2008-04-14
> **benpage26 said:**
> Hi pt_lam,

Since i posted this I have been trying to sort out the heat problems.  For now I have given up.  I just keep an eye and shut down the laptop whenever it gets too hot.  Shame really.I see that you are a 7.10 user. I had the same heat problems on my HP laptop with 7.04 and miraculously they vanished when I installed 7.10. 

My guess is the newer OS was better at handling "my" machine. For multimedia keys, have you tried setting the Keyboard shortcuts found under System>>Preferences>>Keyboard Shortcuts. Note however, that they won't work for all buttons in all machines. The hex key code that IBM uses for those particular buttons might be different than the standard, leaving you with nowhere to go :(

---

### Post by benpage26 on 2008-04-15
If moving up a version fixed it for you, Maybe if I wait for the next ubuntu release (Isn't it in about a week) some of these problems will be fixed then.

I will also look into the Synaptic Package Manager for laptop packages ^^ Thanks.

---

### Post by pt_lam on 2008-04-15
> **benpage26 said:**
> If moving up a version fixed it for you, Maybe if I wait for the next ubuntu release (Isn't it in about a week) some of these problems will be fixed then.

I will also look into the Synaptic Package Manager for laptop packages ^^ Thanks.

Same view here. I'm just looking forward that the new version of ubuntu could fix my problem.

---

### Post by sneeks on 2008-04-15
you may want to wait a few weeks after release as this gives them time to iron things out.

---

### Post by shardzero on 2008-04-28
Hi there,

well I've got almost an identical notebook like you, ben, and likewise the same problems.
The only difference is that I have a Satellite (not a tablet pc).
I tried many things to get rid of the heat problem, installed the toshutils (aka Toshiba utilities) which are actually not for this notebook generation with a Phoenix BIOS, and also the Omnibook drivers which are supposed to work with our laptop model. But the latter would not load into the kernel saying something of an invalid param "apmenu".
Could not find anything about that on the net not in the code by grepping through it...
Anyway after that I was really worrying about the heat 'cause it really felt hot and the fan was almost silent. And it was REALLY hot as I found out after installing and opening gkrellm. Both sensors showed over 80°celsius!
Surprisingly short after I opened gkrellm my fan started to finally cool down the system to less than 50 at first, and now its less than 45° on both sensors.
I wonder what could've triggered that @_@.
Maybe you should install that app, too, and see if your fan starts spinning, too.

As for the other issues:
- xev & the multimedia buttons show the same thing -> nothing
- haven't tried the TV-Out yet, but the monitor output can't be configured correctly using that simple desktop resolution "applet". Trying the better displayconfig-gtk soon. Why did they delete the shortcut to it anyway?
- the display brightness is also not controllable, neither with the applet, nor the FN-Key combination, nor the power configuration dialog. And when it should "darken" the screen due to inactivity, it just makes it black, but the display backlight is still on.

But still, the standby and the, as I call it, rip state (hybernation to disk) work fine for me...
Maybe 'cause my WLAN-card is always hard-switched off?

It's just a shame that the power saving features aren't that good as in Winidiot *damn manufacturers*.

Anyway, if anyone need any pieces of information for fixing this I'd gladly provide it.

Greetz,
Shardzero

---

### Post by benpage26 on 2008-04-29
> **shardzero said:**
> Hi there ...

Hi,

Since i have had the laptop i have also experimented with the  toshutils/omnibook modules, I didn't have much luck with either.  I've just installed gkrellm and I shall see what happens.  

A while ago i found this resource: [http://gentoo-wiki.com/HOWTO_Use_Multimedia_Keys#Determine_the_keycodes](http://gentoo-wiki.com/HOWTO_Use_Multimedia_Keys#Determine_the_keycodes) that detailed how to setup keys that xev cannot see, i never had much luck with it myself, YMMV.

While re-reading the page about scan codes i ran dmesg | tail and saw some worrying output:
```

$ dmesg | tail
[  107.179290] ACPI: Transitioning device [FAN0] to D0
[  107.179297] ACPI: Transitioning device [FAN0] to D0
[  107.179300] ACPI: Unable to turn cooling device [f7c47468] 'on'
[  109.176364] ACPI: Transitioning device [FAN0] to D0
[  109.176371] ACPI: Transitioning device [FAN0] to D0
[  109.176373] ACPI: Unable to turn cooling device [f7c47468] 'on'
[  111.173411] ACPI: Transitioning device [FAN0] to D0
[  111.173418] ACPI: Transitioning device [FAN0] to D0
[  111.173421] ACPI: Unable to turn cooling device [f7c47468] 'on'

```

Did you ever get output like that?

I will try hibernate and standby with my WLAN card turned off and see if that makes any difference.

Thanks, ben.

(PS. My toshiba is a notebook not a tablet PC, i thought Sattelite/Equium were the same thing)

---

### Post by shardzero on 2008-04-30
> **benpage26 said:**
> Hi,

Since i have had the laptop i have also experimented with the  toshutils/omnibook modules, I didn't have much luck with either.  I've just installed gkrellm and I shall see what happens.  

A while ago i found this resource: [http://gentoo-wiki.com/HOWTO_Use_Multimedia_Keys#Determine_the_keycodes](http://gentoo-wiki.com/HOWTO_Use_Multimedia_Keys#Determine_the_keycodes) that detailed how to setup keys that xev cannot see, i never had much luck with it myself, YMMV.

While re-reading the page about scan codes i ran dmesg | tail and saw some worrying output:
```

$ dmesg | tail
[  107.179290] ACPI: Transitioning device [FAN0] to D0
[  107.179297] ACPI: Transitioning device [FAN0] to D0
[  107.179300] ACPI: Unable to turn cooling device [f7c47468] 'on'
[  109.176364] ACPI: Transitioning device [FAN0] to D0
[  109.176371] ACPI: Transitioning device [FAN0] to D0
[  109.176373] ACPI: Unable to turn cooling device [f7c47468] 'on'
[  111.173411] ACPI: Transitioning device [FAN0] to D0
[  111.173418] ACPI: Transitioning device [FAN0] to D0
[  111.173421] ACPI: Unable to turn cooling device [f7c47468] 'on'

```

Did you ever get output like that?

I will try hibernate and standby with my WLAN card turned off and see if that makes any difference.

Thanks, ben.

(PS. My toshiba is a notebook not a tablet PC, i thought Sattelite/Equium were the same thing)

Oh, I thought it would be 'cause your xorg.conf has those wacom input devices commented "# Tablet PC ONLY" which I don't have, I've just got the synaptics touchpad.

Anyway, will take a look at that gentoo wiki, thanks for the tip.

About the error messages: had to grep through dmesg, but also found them.

```
dmesg | grep 'ACPI: Unable'
[   20.729451] ACPI: Unable to turn cooling device [f7c46450] 'on'
[   46.438803] ACPI: Unable to turn cooling device [f7c46450] 'on'
[   46.443758] ACPI: Unable to turn cooling device [f7c46450] 'on'
```

Well as you see those are in a quite early stage after the boot and I usually execute gkrellm directly after logging in so maybe that's why it does not show after?
Don't know, but I'll keep an eye on it.

Edit: Stuff mentioned in the gentoo wiki didn't work out for me either...

---

### Post by funfrank on 2008-06-12
I also have a toshiba satellite a105. it was overheating like some others in this post. here's what I did:

1. turn it upside down and look at the fan.  

2. check to see if it is spinning. it may be blocked with a big hairball, seriously.

3. if it is, get a pen knife - the kind that cuts plastic easily - e.g. the kind used for building plastic models.

4. turn the machine off, and cut out two or three laterals of the grid that covers the fan.

5. move the fan into position with two pencils, one section of the fan at a time, until the section with the hairball is in the slot you cut in step 4. 

6. take the hairball out with a pair of tweezers.

I'm serious. my fan started spinning again, and my toshiba hasn't overheated since. alternatively, you can take the laptop apart, but cutting it with a knife is more gratifying, and a lot simpler.

I performed this operation (haha) when I was using XP, and my fan functions without problem using Hardy. Point is, it may not be a software problem for you either.

My teething problems with this computer are the microphone and hibernation. no luck with the forums. apparently, the mic problem is an alsa-utils bug, which hopefully will be fixed with the next kernel release.

funfrank

---

### Post by benpage26 on 2008-06-22
> **funfrank said:**
> I also have a toshiba satellite a105. it was overheating like some others in this post. here's what I did:

1. turn it upside down and look at the fan.  

2. check to see if it is spinning. it may be blocked with a big hairball, seriously.

3. if it is, get a pen knife - the kind that cuts plastic easily - e.g. the kind used for building plastic models.

4. turn the machine off, and cut out two or three laterals of the grid that covers the fan.

5. move the fan into position with two pencils, one section of the fan at a time, until the section with the hairball is in the slot you cut in step 4. 

6. take the hairball out with a pair of tweezers.

I'm serious. my fan started spinning again, and my toshiba hasn't overheated since. alternatively, you can take the laptop apart, but cutting it with a knife is more gratifying, and a lot simpler.

I performed this operation (haha) when I was using XP, and my fan functions without problem using Hardy. Point is, it may not be a software problem for you either.

My teething problems with this computer are the microphone and hibernation. no luck with the forums. apparently, the mic problem is an alsa-utils bug, which hopefully will be fixed with the next kernel release.

funfrank

Thanks, but unfortuatley for me this does seem to be a software problem, all the fans are spinning :(

---

