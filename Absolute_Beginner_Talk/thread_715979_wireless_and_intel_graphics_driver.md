---
title: "wireless and intel graphics driver"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by gareth_1985 on 2008-03-05
Hi I am a complete newbie. 

I have just installed Ubunto 7.10 Gutsy Gibbon on a Toshiba A200-1V0 laptop. Everything seems fine but I have 2 problems:

1. On networking there is no wireless networking (the laptop has an internal wifi card which was working fine on vista)
2. How do I install graphics driver for Intel GMA X3100

Following some advice I have typer the following commands into the terminal:

**lspci**
**[COLOR="Red"]sudo lshw[/COLOR]**
**[COLOR="Blue"]cat /etc/X11/xorg.conf[/COLOR]**
And the following is what I get from typing these commands, any help on which/how drivers to install would be much appreciated.
 
**lspci**
laptop@Lydia-and-Gareth:~$ lspci 
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03) 
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03) 
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03) 
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03) 
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03) 
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) 
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03) 
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) 
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03) 
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03) 
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03) 
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03) 
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) 
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) 
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) 
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) 
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03) 
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) 
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03) 
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03) 
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14) 
laptop@Lydia-and-Gareth:~$ 

[COLOR="red"]**[COLOR="red"]sudo lshw[/COLOR]**
laptop@Lydia-and-Gareth:~$ sudo lshw 
[sudo] password for laptop: 
lydia-and-gareth 
description: Computer 
product: EQUIUM A200 
vendor: TOSHIBA 
version: PSAF5E-002005KS 
serial: Y7102780Q 
width: 32 bits 
capabilities: smbios-2.4 dmi-2.4 
configuration: boot=oem-specific uuid=31D7A5C0-8E01-11DC-A70E-00A0D18BB632 
*-core 
description: Motherboard 
product: SANTA ROSA CRB 
vendor: Intel Corporation 
physical id: 0 
version: Not Applicable 
serial: Not Applicable 
*-firmware 
description: BIOS 
vendor: Phoenix Technologies LTD 
physical id: 0 
version: 1.60 (10/05/2007) 
size: 104KB 
capacity: 960KB 
capabilities: isa pci pcmcia pnp upgrade shadowing escd cdboot acpi usb agp biosbootspecification 
*-cpu 
description: CPU 
product: Intel(R) Pentium(R) Dual CPU T2310 @ 1.46GHz 
vendor: Intel Corp. 
physical id: 4 
bus info: cpu@0 
version: 6.15.13 
serial: 0000-06FD-0000-0000-0000-0000 
slot: U2E1 
size: 1467MHz 
capacity: 4096MHz 
width: 64 bits 
capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm cpufreq 
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
size: 1MB 
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
physical id: 9 
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
version: 03 
width: 32 bits 
clock: 33MHz 
configuration: driver=agpgart-intel module=intel_agp 
*-display:0 
description: VGA compatible controller 
product: Mobile GM965/GL960 Integrated Graphics Controller 
vendor: Intel Corporation 
physical id: 2 
bus info: pci@0000:00:02.0 
version: 03 
width: 64 bits 
clock: 33MHz 
capabilities: msi pm vga bus_master cap_list 
configuration: latency=0 
*-display:1 UNCLAIMED 
description: Display controller 
product: Mobile GM965/GL960 Integrated Graphics Controller 
vendor: Intel Corporation 
physical id: 2.1 
bus info: pci@0000:00:02.1 
version: 03 
width: 64 bits 
clock: 33MHz 
capabilities: pm bus_master cap_list 
configuration: latency=0 
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
*-multimedia 
description: Audio device 
product: 82801H (ICH8 Family) HD Audio Controller 
vendor: Intel Corporation 
physical id: 1b 
bus info: pci@0000:00:1b.0 
version: 03 
width: 64 bits 
clock: 33MHz 
capabilities: pm msi pciexpress bus_master cap_list 
configuration: driver=HDA Intel latency=0 module=snd_hda_intel 
*-pci:0 
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
*-network 
description: Ethernet interface 
product: 88E8039 PCI-E Fast Ethernet Controller 
vendor: Marvell Technology Group Ltd. 
physical id: 0 
bus info: pci@0000:02:00.0 
logical name: eth0 
version: 14 
serial: 00:a0:d1:8b:b6:32 
capacity: 100MB/s 
width: 64 bits 
clock: 33MHz 
capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.18 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair 
*-pci:1 
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
*-pci:2 
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
*-pci:3 
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
*-pci:4 
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
*-pci:5 
description: PCI bridge 
product: 82801 Mobile PCI Bridge 
vendor: Intel Corporation 
physical id: 1e 
bus info: pci@0000:00:1e.0 
version: f3 
width: 32 bits 
clock: 33MHz 
capabilities: pci subtractive_decode bus_master cap_list 
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
logical name: scsi0 
version: 03 
width: 32 bits 
clock: 33MHz 
capabilities: ide bus_master emulated 
configuration: driver=ata_piix latency=0 module=ata_piix 
*-cdrom 
description: DVD-RAM writer 
product: CDDVDW TS-L632H 
vendor: TSSTcorp 
physical id: 0.0.0 
bus info: scsi@0:0.0.0 
logical name: /dev/cdrom 
logical name: /dev/dvd 
logical name: /dev/scd0 
logical name: /dev/sr0 
version: TO01 
capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram 
configuration: ansiversion=5 status=open 
*-storage 
description: SATA controller 
product: 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller 
vendor: Intel Corporation 
physical id: 1f.2 
bus info: pci@0000:00:1f.2 
logical name: scsi2 
version: 03 
width: 32 bits 
clock: 66MHz 
capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated 
configuration: driver=ahci latency=0 module=ahci 
*-disk 
description: SCSI Disk 
product: ST9120822AS 
vendor: ATA 
physical id: 0.0.0 
bus info: scsi@2:0.0.0 
logical name: /dev/sda 
version: 3.AL 
serial: 5LZ6M9QN 
size: 111GB 
capabilities: partitioned partitioned:dos 
configuration: ansiversion=5 
*-volume:0 
description: Linux filesystem partition 
physical id: 1 
bus info: scsi@2:0.0.0,1 
logical name: /dev/sda1 
capacity: 107GB 
capabilities: primary bootable 
*-volume:1 
description: Extended partition 
physical id: 2 
bus info: scsi@2:0.0.0,2 
logical name: /dev/sda2 
size: 4690MB 
capacity: 4690MB 
capabilities: primary extended partitioned partitioned:extended 
*-logicalvolume 
description: Linux swap / Solaris partition 
physical id: 5 
logical name: /dev/sda5 
capacity: 4690MB 
capabilities: nofs 
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
*-scsi 
physical id: 1 
bus info: usb@7:2 
logical name: scsi11 
capabilities: emulated scsi-host 
configuration: driver=usb-storage 
*-disk 
description: SCSI Disk 
product: TS1GJFV35 
vendor: JetFlash 
physical id: 0.0.0 
bus info: scsi@11:0.0.0 
logical name: /dev/sdb 
version: 8.07 
size: 969MB 
capabilities: removable 
configuration: ansiversion=2 
*-disc 
physical id: 0 
logical name: /dev/sdb 
size: 969MB 
capabilities: partitioned partitioned:dos 
*-volume 
description: FAT16 partition 
physical id: 1 
logical name: /dev/sdb1 
capacity: 969MB 
capabilities: primary 
laptop@Lydia-and-Gareth:~$ [/COLOR] 

[COLOR="blue"]**cat /etc/X11/xorg.conf**
laptop@Lydia-and-Gareth:~$ cat /etc/X11/xorg.conf 
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
# sudo dpkg-reconfigure -phigh xserver-xorg 

Section "Files" 
EndSection 

Section "InputDevice" 
Identifier "Generic Keyboard" 
Driver "kbd" 
Option "CoreKeyboard" 
Option "XkbRules" "xorg" 
Option "XkbModel" "pc105" 
Option "XkbLayout" "gb" 
EndSection 

Section "InputDevice" 
Identifier "Configured Mouse" 
Driver "mouse" 
Option "CorePointer" 
Option "Device" "/dev/input/mice" 
Option "Protocol" "ImPS/2" 
Option "ZAxisMapping" "4 5" 
Option "Emulate3Buttons" "true" 
EndSection 

Section "InputDevice" 
Identifier "Synaptics Touchpad" 
Driver "synaptics" 
Option "SendCoreEvents" "true" 
Option "Device" "/dev/psaux" 
Option "Protocol" "auto-dev" 
Option "HorizEdgeScroll" "0" 
EndSection 

Section "InputDevice" 
Driver "wacom" 
Identifier "stylus" 
Option "Device" "/dev/input/wacom" 
Option "Type" "stylus" 
Option "ForceDevice" "ISDV4" # Tablet PC ONLY 
EndSection 

Section "InputDevice" 
Driver "wacom" 
Identifier "eraser" 
Option "Device" "/dev/input/wacom" 
Option "Type" "eraser" 
Option "ForceDevice" "ISDV4" # Tablet PC ONLY 
EndSection 

Section "InputDevice" 
Driver "wacom" 
Identifier "cursor" 
Option "Device" "/dev/input/wacom" 
Option "Type" "cursor" 
Option "ForceDevice" "ISDV4" # Tablet PC ONLY 
EndSection 

Section "Device" 
Identifier "Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller" 
Driver "intel" 
BusID "PCI:0:2:0" 
EndSection 

Section "Monitor" 
Identifier "Generic Monitor" 
Option "DPMS" 
EndSection 

Section "Screen" 
Identifier "Default Screen" 
Device "Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller" 
Monitor "Generic Monitor" 
DefaultDepth 24 
SubSection "Display" 
Modes "1280x800" 
EndSubSection 
EndSection 

Section "ServerLayout" 
Identifier "Default Layout" 
Screen "Default Screen" 
InputDevice "Generic Keyboard" 
InputDevice "Configured Mouse" 

# Uncomment if you have a wacom tablet 
# InputDevice "stylus" "SendCoreEvents" 
# InputDevice "cursor" "SendCoreEvents" 
# InputDevice "eraser" "SendCoreEvents" 
InputDevice "Synaptics Touchpad" 
EndSection 
laptop@Lydia-and-Gareth:~$[/COLOR]

---

### Post by neurostu on 2008-03-05
Have checked the Restricted Driver Manager to see if there are drivers waiting to be installed? 

Check by going System->Administration -> Restricted Drivers Manager.

I am pretty sure there will be  driver for the wireless card, possibly for the video card.  I'm not to sure though. I haven't heard of anyone needing a specific driver for an Intel card, most people have to install a driver if they are running an Nvidia or ATI card but maybe you need one for intel too...

---

### Post by gareth_1985 on 2008-03-05
I have checked restricted driver manager and it says "your hardware does not need any restricted drivers."
Any other ideas?
Thanks

---

### Post by norsk on 2008-03-09
You can keep semi-up-to-date with X3100 drivers by following this thread: [http://ubuntuforums.org/showthread.php?t=674643&highlight=x3100](http://ubuntuforums.org/showthread.php?t=674643&highlight=x3100)

---

### Post by igknighted on 2008-03-09
No wireless card is being reported as attached via a PCI bus (where an internal card would be attached).  It works in windows you say?  Could you boot to windows and go to control panel -> system -> device manager and find your wireless adapter (under Network adapters) and tell us what it says it is?  Since everything else is intel, I suspect it also is intel.

Before you go nuts trying to figure it out... have you clicked the networking applet in the systray yet?  If it is detecting wireless networks they will show up then.

One final thought... could you run ifconfig and iwconfig to see if the networking subsystems see a wireless network card?

---

### Post by igknighted on 2008-03-09
> **neurostu said:**
> Have checked the Restricted Driver Manager to see if there are drivers waiting to be installed? 

Check by going System->Administration -> Restricted Drivers Manager.

I am pretty sure there will be  driver for the wireless card, possibly for the video card.  I'm not to sure though. I haven't heard of anyone needing a specific driver for an Intel card, most people have to install a driver if they are running an Nvidia or ATI card but maybe you need one for intel too...

Intel vid-cards use open source drivers (intel releases the specs), so there is no "restricted" driver.  Open source != works perfectly though, there are many bugs with the intel drivers.  Staying with the latest (as linked a few posts up) is preferable.

---

