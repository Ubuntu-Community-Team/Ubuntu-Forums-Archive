---
title: "Virtual Box"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by .adma on 2007-05-29
*****UPDATE*****SOLVED**
All, just follow the link at the bottom. It is the best way to get this installed is to follow the link I have down at the bottom. The only think I did different, is instead of running the command



```
sudo dpkg -i xxxxxxx
```

I just opened the file from my desktop and it installed all of the dependencies properly.

[http://www.ubuntu-unleashed.com/2008...rdy-heron.html](http://www.ubuntu-unleashed.com/2008...rdy-heron.html)
[B]
By the way, THIS ENABLES USB SUPPORT!!![/B]


*******************************************


So, I couldnt get VBOX to run... found out, the new linux kernel generic headers are not available apparently?  So the kernel issues I had with the latest version went away when I went back to the last kernel version.  Does anyone know a fix for this?  Or do I just have to wait until the new kernel headers are available??

---

### Post by Happy_Man on 2007-05-29
Nope, just restart Virtualbox twice, it should go away.

---

### Post by nrgtek on 2007-05-29
> **Happy_Man said:**
> Nope, just restart Virtualbox twice, it should go away.

That doesn't work...

```

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Re-setup the kernel module by executing '/etc/init.d/vboxdrv setup' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}


```

---

### Post by bodhi.zazen on 2007-05-29
Open a terminal,

Enter this command twice (I do not know why it does not work on the first try :twisted: )

```
sudo /etc/init.d/vboxdrv setup
```

If that fails, you need to install the kernel headers :

```
sudo aptitude install linux-headers-$(uname -r)
sudo /etc/init.d/vboxdrv setup
sudo /etc/init.d/vboxdrv setup
```

---

### Post by .adma on 2007-05-29
> **bodhi.zazen said:**
> Open a terminal,

Enter this command twice (I do not know why it does not work on the first try :twisted: )

```
sudo /etc/init.d/vboxdrv setup
```

If that fails, you need to install the kernel headers :

```
sudo aptitude install linux-headers-$(uname -r)
sudo /etc/init.d/vboxdrv setup
sudo /etc/init.d/vboxdrv setup
```

Hmm..I did both of these, but I still get an error when I load with 20-16...20-15 works fine...any other ideas, do I need to tell VBox to use the new kernel?

---

### Post by inanimous on 2007-06-06
doing "sudo /etc/init.d/vboxdrv setup " twice worked for me - why though - what kind of @#$@ is that supposed to be?

oh well. thanks!!!!!!!!!!!!!!

---

### Post by .adma on 2007-06-06
Do you have the latest kernel inanimous?

---

### Post by bodhi.zazen on 2007-06-06
> **inanimous said:**
> doing "sudo /etc/init.d/vboxdrv setup " twice worked for me - why though - what kind of @#$@ is that supposed to be?

oh well. thanks!!!!!!!!!!!!!!

:lolflag:

Yea, it is funky.

> **.adma said:**
> Do you have the latest kernel inanimous?

I do, and then some. VirtualBox up and running on the generic and low latency kernel both, current and previous versions.

---

### Post by Seisen on 2007-06-06
I had the same problem and following those directions fixed the problem.

---

### Post by captlogic on 2007-06-13
I seem to have the same problem, but running the code twice does not help

here's what I get at terminal

patrick@Dublin:~$ sudo aptitude install linux-headers-$(uname -r)
Password:
Sorry, try again.
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
patrick@Dublin:~$ sudo /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel module vboxdrv                             [ OK ] 
 * Recompiling VirtualBox kernel module vboxdrv                          [ OK ] 
 * Starting VirtualBox kernel module vboxdrv                                    FATAL: Error inserting vboxdrv (/lib/modules/2.6.20-16-generic/misc/vboxdrv.ko): Invalid argument

 * Modprobe vboxdrv failed. Please use 'dmesg' to find out why.
patrick@Dublin:~$ sudo /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel module vboxdrv                             [ OK ] 
 * Recompiling VirtualBox kernel module vboxdrv                          [ OK ] 
 * Starting VirtualBox kernel module vboxdrv                                    FATAL: Error inserting vboxdrv (/lib/modules/2.6.20-16-generic/misc/vboxdrv.ko): Invalid argument


Anybody??

---

### Post by myname on 2007-06-14
I am running on Edgy, and after one of the kernel updates in Edgy, Virtual box stopped loading my windows install for me with the same error.

Virtual Box loads, but when I try to start Windows from within VB, I get the following:

> 
VirtualBox kernel driver not installed.
At '/home/vbox/vbox/src/VBox/VMM/VM.cpp' (303) in int VMR3Create(void (*)(VM*, void*, int, const char*, unsigned int, const char*, const char*, char*), void*, int (*)(VM*, void*), void*, VM**).
VBox status code: -1908 VERR_VM_DRIVER_NOT_INSTALLED
.


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}


i tried the above statements, and still get the same error.

Here is my output:

> 
~$ sudo aptitude install linux-headers-$(uname -r)
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
~$ sudo /etc/init.d/vboxdrv setup
sudo: /etc/init.d/vboxdrv: command not found
~$ sudo /etc/init.d/vboxdrv setup
sudo: /etc/init.d/vboxdrv: command not found


any ideas why the vboxdrv is not found?

--Kevin

EDIT...
I updated Virtual box via apt-get, and all is working.

---

### Post by captlogic on 2007-06-15
Auugh!

I've tried to update/install/reconfig virtuabox every which way I can and it still won't work.

I'm still under the assumption that I'd doing something wrong, I'm getting the same error every time
Virtualbox starts, but when I try to run the vm I get the following error.


VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Re-setup the kernel module by executing '/etc/init.d/vboxdrv setup' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

All my research leads me to posts saying I should run the setup twice, but still I keep getting the following error.  I have no idea what it means.

* Recompiling VirtualBox kernel module vboxdrv [ OK ]
* Starting VirtualBox kernel module vboxdrv FATAL: Error inserting vboxdrv (/lib/modules/2.6.20-16-generic/misc/vboxdrv.ko): Invalid argument

I also have vmware server installed, is there an incompatibility?

I'm willing to post any log file, etc that would help.  I just don't know my way around linux well enough to know what to do.

Starting to get desperate  :(

---

### Post by captlogic on 2007-06-15
after I run the setup and get the err message, and run dmesg I get:

[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003fefc000 end: 000000003fffc000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000003fffc000 size: 0000000000003000 end: 000000003ffff000 type: 3
[    0.000000] copy_e820_map() start: 000000003ffff000 size: 0000000000001000 end: 0000000040000000 type: 4
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000001000 end: 00000000fec01000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
[    0.000000] copy_e820_map() start: 00000000ffff0000 size: 0000000000010000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fffc000 (usable)
[    0.000000]  BIOS-e820: 000000003fffc000 - 000000003ffff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ffff000 - 0000000040000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 262140) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   262140
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   262140
[    0.000000] On node 0 totalpages: 262140
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 255 pages used for memmap
[    0.000000]   HighMem zone: 32509 pages, LIFO batch:7
[    0.000000] DMI 2.3 present.
[    0.000000] ASUS P4B266 detected: force use of acpi=ht
[    0.000000] ACPI: RSDP (v000 ASUS                                  ) @ 0x000f7400
[    0.000000] ACPI: RSDT (v001 ASUS   P4B266LM 0x42302e31 MSFT 0x31313031) @ 0x3fffc000
[    0.000000] ACPI: FADT (v001 ASUS   P4B266LM 0x42302e31 MSFT 0x31313031) @ 0x3fffc100
[    0.000000] ACPI: BOOT (v001 ASUS   P4B266LM 0x42302e31 MSFT 0x31313031) @ 0x3fffc040
[    0.000000] ACPI: MADT (v001 ASUS   P4B266LM 0x42302e31 MSFT 0x31313031) @ 0x3fffc080
[    0.000000] ACPI: DSDT (v001   ASUS P4B266LM 0x00001000 MSFT 0x0100000b) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0xe408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:1 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
[    0.000000] Detected 1816.305 MHz processor.
[   13.557880] Built 1 zonelists.  Total pages: 260093
[   13.557887] Kernel command line: root=UUID=8ec7274e-4f20-4a50-9bfe-0e5df434e7d3 ro quiet splash
[   13.558126] Found and enabled local APIC!
[   13.558130] mapped APIC to ffffd000 (fee00000)
[   13.558134] Enabling fast FPU save and restore... done.
[   13.558139] Enabling unmasked SIMD FPU exception support... done.
[   13.558158] Initializing CPU#0
[   13.558270] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   13.560115] Console: colour VGA+ 80x25
[   13.561025] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   13.562367] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   13.609331] Memory: 1028364k/1048560k available (1992k kernel code, 19472k reserved, 900k data, 328k init, 131056k highmem)
[   13.609347] virtual kernel memory layout:
[   13.609349]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   13.609350]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   13.609352]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   13.609353]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   13.609355]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   13.609356]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[   13.609358]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[   13.609362] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   13.686098] Calibrating delay using timer specific routine.. 3636.06 BogoMIPS (lpj=7272134)
[   13.686173] Security Framework v1.0.0 initialized
[   13.686189] SELinux:  Disabled at boot.
[   13.686215] Mount-cache hash table entries: 512
[   13.686477] CPU: After generic identify, caps: 3febfbff 00000000 00000000 00000000 00000000 00000000 00000000
[   13.686496] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   13.686500] CPU: L2 cache: 256K
[   13.686504] CPU: Hyper-Threading is disabled
[   13.686507] CPU: After all inits, caps: 3febfbff 00000000 00000000 00003080 00000000 00000000 00000000
[   13.686528] Compat vDSO mapped to ffffe000.
[   13.686535] Remapping vsyscall page to ffffe000
[   13.686555] Checking 'hlt' instruction... OK.
[   13.702263] SMP alternatives: switching to UP code
[   13.702605] Freeing SMP alternatives: 11k freed
[   13.702959] Early unpacking initramfs... done
[   14.149959] CPU0: Intel(R) Pentium(R) 4 CPU 1.80GHz stepping 02
[   14.150019] Total of 1 processors activated (3636.06 BogoMIPS).
[   14.257360] Brought up 1 CPUs
[   14.257747] Booting paravirtualized kernel on bare hardware
[   14.257869] Time: 23:01:14  Date: 05/14/107
[   14.257918] NET: Registered protocol family 16
[   14.258100] EISA bus registered
[   14.260059] PCI: PCI BIOS revision 2.10 entry at 0xf13e0, last bus=2
[   14.260062] PCI: Using configuration type 1
[   14.260065] Setting up standard PCI resources
[   14.270903] ACPI: Interpreter disabled.
[   14.270909] Linux Plug and Play Support v0.97 (c) Adam Belay
[   14.270924] pnp: PnP ACPI: disabled
[   14.270930] PnPBIOS: Scanning system for PnP BIOS support...
[   14.270979] PnPBIOS: Found PnP BIOS installation structure at 0xc00fc330
[   14.270984] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xc360, dseg 0xf0000
[   14.271945] PnPBIOS: 13 nodes reported by PnP BIOS; 13 recorded by driver
[   14.272027] PCI: Probing PCI hardware
[   14.272038] PCI: Probing PCI hardware (bus 00)
[   14.272325] PCI: Enabled i801 SMBus device
[   14.272335] PCI quirk: region e400-e47f claimed by ICH4 ACPI/GPIO/TCO
[   14.272340] PCI quirk: region ec00-ec3f claimed by ICH4 GPIO
[   14.272699] Boot video device is 0000:01:00.0
[   14.273386] PCI: Transparent bridge - 0000:00:1e.0
[   14.274613] PCI: Using IRQ router PIIX/ICH [8086/2440] at 0000:00:1f.0
[   14.285012] NET: Registered protocol family 8
[   14.285016] NET: Registered protocol family 20
[   14.285155] pnp: 00:12: ioport range 0x290-0x297 has been reserved
[   14.285160] pnp: 00:12: ioport range 0x3f0-0x3f1 has been reserved
[   14.285166] pnp: 00:12: ioport range 0xe400-0xe47f has been reserved
[   14.285170] pnp: 00:12: ioport range 0xec00-0xec3f has been reserved
[   14.285759] PCI: Bridge: 0000:00:01.0
[   14.285763]   IO window: disabled.
[   14.285770]   MEM window: de000000-dfefffff
[   14.285775]   PREFETCH window: dff00000-f7ffffff
[   14.285783] PCI: Bridge: 0000:00:1e.0
[   14.285789]   IO window: b000-dfff
[   14.285796]   MEM window: da800000-ddffffff
[   14.285802]   PREFETCH window: disabled.
[   14.285818] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   14.285832] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   14.285881] NET: Registered protocol family 2
[   14.313330] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   14.313661] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   14.315322] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   14.316261] TCP: Hash tables configured (established 131072 bind 65536)
[   14.316269] TCP reno registered
[   14.325469] checking if image is initramfs... it is
[   15.202184] Freeing initrd memory: 6783k freed
[   15.202507] Simple Boot Flag at 0x3a set to 0x1
[   15.202858] audit: initializing netlink socket (disabled)
[   15.202879] audit(1181862074.724:1): initialized
[   15.203018] highmem bounce pool size: 64 pages
[   15.203148] VFS: Disk quotas dquot_6.5.1
[   15.203182] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   15.203277] io scheduler noop registered
[   15.203282] io scheduler anticipatory registered
[   15.203285] io scheduler deadline registered
[   15.203306] io scheduler cfq registered (default)
[   15.203733] isapnp: Scanning for PnP cards...
[   15.557510] isapnp: No Plug & Play device found
[   15.641422] Real Time Clock Driver v1.12ac
[   15.641548] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   15.643522] mice: PS/2 mouse device common for all mice
[   15.644515] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   15.644870] input: Macintosh mouse button emulation as /class/input/input0
[   15.644935] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   15.644941] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   15.645299] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[   15.647764] serio: i8042 KBD port at 0x60,0x64 irq 1
[   15.647772] serio: i8042 AUX port at 0x60,0x64 irq 12
[   15.648000] EISA: Probing bus 0 at eisa.0
[   15.648043] EISA: Detected 0 cards.
[   15.678148] TCP cubic registered
[   15.678169] NET: Registered protocol family 1
[   15.678299] Testing NMI watchdog ... OK.
[   15.717980] Using IPI No-Shortcut mode
[   15.718021]   Magic number: 11:453:49
[   15.718781] Freeing unused kernel memory: 328k freed
[   15.719245] Time: tsc clocksource has been installed.
[   17.227972] Capability LSM initialized
[   17.317972] thermal: Unknown symbol acpi_processor_set_thermal_limit
[   18.334129] SCSI subsystem initialized
[   18.343474] libata version 2.20 loaded.
[   18.349233] ata_piix 0000:00:1f.1: version 2.10ac1
[   18.349275] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   18.349355] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001a800 irq 14
[   18.349400] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001a808 irq 15
[   18.349437] scsi0 : ata_piix
[   18.363196] usbcore: registered new interface driver usbfs
[   18.363235] usbcore: registered new interface driver hub
[   18.363277] usbcore: registered new device driver usb
[   18.364927] USB Universal Host Controller Interface driver v3.0
[   18.454281] ieee1394: Initialized config rom entry `ip1394'
[   18.465342] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   18.494294] 8139too Fast Ethernet driver 0.9.28
[   18.532268] Floppy drive(s): fd0 is 1.44M
[   18.545531] ata1.00: ata_hpa_resize 1: sectors = 312581808, hpa_sectors = 312581808
[   18.545539] ata1.00: ATA-7: WDC WD1600JB-00REA0, 20.00K20, max UDMA/100
[   18.545544] ata1.00: 312581808 sectors, multi 16: LBA48 
[   18.555535] ata1.00: ata_hpa_resize 1: sectors = 312581808, hpa_sectors = 312581808
[   18.555542] ata1.00: configured for UDMA/100
[   18.555561] scsi1 : ata_piix
[   18.632884] FDC 0 is a post-1991 82077
[   18.878844] ata2.00: ATAPI, max UDMA/33
[   19.046610] ata2.00: configured for UDMA/33
[   19.046805] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600JB-00R 20.0 PQ: 0 ANSI: 5
[   19.047173] scsi 1:0:0:0: CD-ROM            LITE-ON  LTR-24102B       5S54 PQ: 0 ANSI: 5
[   19.049089] PCI: setting IRQ 10 as level-triggered
[   19.049097] PCI: Found IRQ 10 for device 0000:00:1f.2
[   19.049138] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   19.049144] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[   19.049324] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[   19.049360] uhci_hcd 0000:00:1f.2: irq 10, io base 0x0000a400
[   19.049540] usb usb1: configuration #1 chosen from 1 choice
[   19.049585] hub 1-0:1.0: USB hub found
[   19.049598] hub 1-0:1.0: 2 ports detected
[   19.072833] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[   19.072874] sda: Write Protect is off
[   19.072878] sda: Mode Sense: 00 3a 00 00
[   19.072906] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   19.073005] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[   19.073021] sda: Write Protect is off
[   19.073024] sda: Mode Sense: 00 3a 00 00
[   19.073051] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   19.073057]  sda: sda1 sda2 sda3 < sda5 sda6 > sda4
[   19.117068] sd 0:0:0:0: Attached scsi disk sda
[   19.124966] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   19.125214] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   19.149781] sr0: scsi3-mmc drive: 186x/40x writer cd/rw xa/form2 cdda tray
[   19.149790] Uniform CD-ROM driver Revision: 3.20
[   19.150176] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   19.154471] PCI: setting IRQ 5 as level-triggered
[   19.154478] PCI: Found IRQ 5 for device 0000:00:1f.4
[   19.154504] PCI: Sharing IRQ 5 with 0000:02:0a.2
[   19.154509] PCI: Sharing IRQ 5 with 0000:02:0b.0
[   19.154527] PCI: Setting latency timer of device 0000:00:1f.4 to 64
[   19.154532] uhci_hcd 0000:00:1f.4: UHCI Host Controller
[   19.154573] uhci_hcd 0000:00:1f.4: new USB bus registered, assigned bus number 2
[   19.154605] uhci_hcd 0000:00:1f.4: irq 5, io base 0x0000a000
[   19.154756] usb usb2: configuration #1 chosen from 1 choice
[   19.154797] hub 2-0:1.0: USB hub found
[   19.154812] hub 2-0:1.0: 2 ports detected
[   19.262422] PCI: Found IRQ 5 for device 0000:02:0a.2
[   19.262442] PCI: Sharing IRQ 5 with 0000:00:1f.4
[   19.262454] PCI: Sharing IRQ 5 with 0000:02:0b.0
[   19.314140] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[5]  MMIO=[dd000000-dd0007ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   19.317658] PCI: Found IRQ 5 for device 0000:02:0b.0
[   19.317677] PCI: Sharing IRQ 5 with 0000:00:1f.4
[   19.317688] PCI: Sharing IRQ 5 with 0000:02:0a.2
[   19.317714] ohci_hcd 0000:02:0b.0: OHCI Host Controller
[   19.317783] ohci_hcd 0000:02:0b.0: new USB bus registered, assigned bus number 3
[   19.317804] ohci_hcd 0000:02:0b.0: irq 5, io mem 0xdc000000
[   19.879700] usb 1-1: new low speed USB device using uhci_hcd and address 2
[   19.880812] usb usb3: configuration #1 chosen from 1 choice
[   19.881269] hub 3-0:1.0: USB hub found
[   19.881293] hub 3-0:1.0: 3 ports detected
[   20.026267] Attempting manual resume
[   20.026273] swsusp: Resume From Partition 8:5
[   20.026276] PM: Checking swsusp image.
[   20.026540] PM: Resume from disk failed.
[   20.063885] usb 1-1: configuration #1 chosen from 1 choice
[   20.094302] kjournald starting.  Commit interval 5 seconds
[   20.094328] EXT3-fs: mounted filesystem with ordered data mode.
[   20.308564] usb 2-1: new low speed USB device using uhci_hcd and address 2
[   20.396595] PCI: setting IRQ 4 as level-triggered
[   20.396602] PCI: Found IRQ 4 for device 0000:02:0b.1
[   20.396655] ohci_hcd 0000:02:0b.1: OHCI Host Controller
[   20.396707] ohci_hcd 0000:02:0b.1: new USB bus registered, assigned bus number 4
[   20.396728] ohci_hcd 0000:02:0b.1: irq 4, io mem 0xdb800000
[   20.962445] usb usb4: configuration #1 chosen from 1 choice
[   20.962489] hub 4-0:1.0: USB hub found
[   20.962506] hub 4-0:1.0: 2 ports detected
[   20.994787] usb 2-1: configuration #1 chosen from 1 choice
[   20.997932] usbcore: registered new interface driver hiddev
[   21.014370] input: Logitech USB Receiver as /class/input/input1
[   21.014402] input: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1f.2-1
[   21.027808] input: Logitech Logitech USB Keyboard as /class/input/input2
[   21.027834] input: USB HID v1.10 Keyboard [Logitech Logitech USB Keyboard] on usb-0000:00:1f.4-1
[   21.031700] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023c0021010623]
[   21.068680] input: Logitech Logitech USB Keyboard as /class/input/input3
[   21.068740] input: USB HID v1.10 Mouse [Logitech Logitech USB Keyboard] on usb-0000:00:1f.4-1
[   21.068764] usbcore: registered new interface driver usbhid
[   21.068769] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   21.479365] PCI: setting IRQ 3 as level-triggered
[   21.479372] PCI: Found IRQ 3 for device 0000:02:0b.2
[   21.479392] PCI: Sharing IRQ 3 with 0000:02:09.0
[   21.479407] PCI: Sharing IRQ 3 with 0000:02:0d.0
[   21.479425] ehci_hcd 0000:02:0b.2: EHCI Host Controller
[   21.479486] ehci_hcd 0000:02:0b.2: new USB bus registered, assigned bus number 5
[   21.506831] ehci_hcd 0000:02:0b.2: irq 3, io mem 0xdb000000
[   21.506844] ehci_hcd 0000:02:0b.2: USB 2.0 started, EHCI 0.95, driver 10 Dec 2004
[   21.506999] usb usb5: configuration #1 chosen from 1 choice
[   21.507042] hub 5-0:1.0: USB hub found
[   21.507056] hub 5-0:1.0: 5 ports detected
[   21.611166] PCI: Found IRQ 3 for device 0000:02:0d.0
[   21.611189] PCI: Sharing IRQ 3 with 0000:02:09.0
[   21.611201] PCI: Sharing IRQ 3 with 0000:02:0b.2
[   21.611579] eth0: RealTek RTL8139 at 0xf88be000, 00:e0:18:67:72:bc, IRQ 3
[   21.611583] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   29.461093] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   31.008898] NET: Registered protocol family 17
[   32.060466] Linux agpgart interface v0.102 (c) Dave Jones
[   32.063178] agpgart: Detected an Intel i845 Chipset.
[   32.067136] agpgart: AGP aperture is 64M @ 0xf8000000
[   32.560410] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   32.570307] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   32.584522] intel_rng: FWH not detected
[   33.059042] input: PC Speaker as /class/input/input4
[   33.077796] iTCO_vendor_support: vendor-support=0
[   33.079601] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   33.120098] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   33.120111] iTCO_wdt: No card detected
[   33.836986] nvidia: module license 'NVIDIA' taints kernel.
[   34.109580] gameport: EMU10K1 is pci0000:02:0a.1/gameport0, io 0xd000, speed 1028kHz
[   34.110813] usbcore: registered new interface driver xpad
[   34.110819] drivers/usb/input/xpad.c: driver for Xbox controllers v0.1.6
[   34.219927] PCI: setting IRQ 11 as level-triggered
[   34.219935] PCI: Found IRQ 11 for device 0000:01:00.0
[   34.220599] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov  9 17:38:10 PST 2006
[   34.400268] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   34.978808] PCI: setting IRQ 7 as level-triggered
[   34.978815] PCI: Found IRQ 7 for device 0000:02:0a.0
[   35.310424] fuse init (API version 7.8)
[   35.394494] lp: driver loaded but no devices found
[   35.493814] Adding 2931820k swap on /dev/disk/by-uuid/aafb28fb-25e1-4d1b-988c-29fb85a120ad.  Priority:-1 extents:1 across:2931820k
[   35.668777] EXT3 FS on sda2, internal journal
[   35.951912] NET: Registered protocol family 10
[   35.952075] lo: Disabled Privacy Extensions
[   36.214731] kjournald starting.  Commit interval 5 seconds
[   36.215026] EXT3 FS on sda4, internal journal
[   36.215034] EXT3-fs: mounted filesystem with ordered data mode.
[   36.254905] NTFS driver 2.1.28 [Flags: R/O MODULE].
[   36.338221] NTFS volume version 3.1.
[   42.470353] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
[   42.470435] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
[   42.470634] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
[   42.470734] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
[   46.022983] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   46.023507] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   46.023848] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[   46.992479] ppdev: user-space parallel port driver
[   47.890315] apm: BIOS version 1.2 Flags 0x0b (Driver version 1.16ac)
[   48.129972] sonypi: Sony Programmable I/O Controller Driver v1.26.
[   51.848396] vboxdrv: Trying to deactivate NMI watchdog permanently...
[   51.848406] vboxdrv: NMI watchdog either active or at least initialized. Please disable the NMI
[   51.848408] vboxdrv: watchdog by specifying 'nmi_watchdog=0' at kernel command line.
[   52.053411] /dev/vmmon[5037]: Module vmmon: registered with major=10 minor=165
[   52.054536] /dev/vmmon[5037]: Module vmmon: initialized
[   52.184020] /dev/vmnet: open called by PID 5064 (vmnet-bridge)
[   52.184450] /dev/vmnet: hub 0 does not exist, allocating memory.
[   52.184816] /dev/vmnet: port on hub 0 successfully opened
[   52.185135] bridge-eth0: enabling the bridge
[   52.185390] bridge-eth0: up
[   52.185587] bridge-eth0: already up
[   52.185806] bridge-eth0: attached
[   52.261590] /dev/vmnet: open called by PID 5078 (vmnet-natd)
[   52.262008] /dev/vmnet: hub 8 does not exist, allocating memory.
[   52.262346] /dev/vmnet: port on hub 8 successfully opened
[   52.616437] Bluetooth: Core ver 2.11
[   52.616529] NET: Registered protocol family 31
[   52.616532] Bluetooth: HCI device and connection manager initialized
[   52.616537] Bluetooth: HCI socket layer initialized
[   52.730898] Bluetooth: L2CAP ver 2.8
[   52.730905] Bluetooth: L2CAP socket layer initialized
[   52.749889] Bluetooth: RFCOMM socket layer initialized
[   52.749910] Bluetooth: RFCOMM TTY layer initialized
[   52.749914] Bluetooth: RFCOMM ver 1.8
[   59.723521] eth0: no IPv6 routers present
[   62.230324] /dev/vmnet: open called by PID 5294 (vmnet-netifup)
[   62.230767] /dev/vmnet: port on hub 8 successfully opened
[   62.250497] /dev/vmnet: open called by PID 5293 (vmnet-netifup)
[   62.250932] /dev/vmnet: hub 1 does not exist, allocating memory.
[   62.251254] /dev/vmnet: port on hub 1 successfully opened
[   62.340053] /dev/vmnet: open called by PID 5315 (vmnet-dhcpd)
[   62.340412] /dev/vmnet: port on hub 1 successfully opened
[   62.360561] /dev/vmnet: open called by PID 5316 (vmnet-dhcpd)
[   62.360918] /dev/vmnet: port on hub 8 successfully opened
[   72.321294] vmnet1: no IPv6 routers present
[   72.728705] vmnet8: no IPv6 routers present
[ 1192.751397] vboxdrv: Trying to deactivate NMI watchdog permanently...
[ 1192.751406] vboxdrv: NMI watchdog either active or at least initialized. Please disable the NMI
[ 1192.751409] vboxdrv: watchdog by specifying 'nmi_watchdog=0' at kernel command line.


I've seen a reference to (passing variables?) to NMI, but don't quite get it?

Thanks in advance to linux gurus.

:)

---

### Post by myname on 2007-06-15
> **captlogic said:**
> Auugh!

I've tried to update/install/reconfig virtuabox every which way I can and it still won't work.

I'm still under the assumption that I'd doing something wrong, I'm getting the same error every time
Virtualbox starts, but when I try to run the vm I get the following error.


VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Re-setup the kernel module by executing '/etc/init.d/vboxdrv setup' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

All my research leads me to posts saying I should run the setup twice, but still I keep getting the following error.  I have no idea what it means.

* Recompiling VirtualBox kernel module vboxdrv [ OK ]
* Starting VirtualBox kernel module vboxdrv FATAL: Error inserting vboxdrv (/lib/modules/2.6.20-16-generic/misc/vboxdrv.ko): Invalid argument

I also have vmware server installed, is there an incompatibility?

I'm willing to post any log file, etc that would help.  I just don't know my way around linux well enough to know what to do.

Starting to get desperate  :(

Have you tried going here: [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)  and following the steps to getting this added to your sources list?  I followed the steps for Edgy, and then did the apt-get from the command line (need to agree to the license agreement) and all worked well.
--Kevin

---

### Post by bodhi.zazen on 2007-06-15
> **captlogic said:**
> after I run the setup and get the err message, and run dmesg I get:

...

[   72.321294] vmnet1: no IPv6 routers present
[   72.728705] vmnet8: no IPv6 routers present
[ 1192.751397] vboxdrv: Trying to deactivate NMI watchdog permanently...
[ 1192.751406] vboxdrv: NMI watchdog either active or at least initialized. Please disable the NMI
[ 1192.751409] vboxdrv: watchdog by specifying 'nmi_watchdog=0' at kernel command line.


I've seen a reference to (passing variables?) to NMI, but don't quite get it?

Thanks in advance to linux gurus.

:)

OMG ~ please consider posting long output like that as an attachment :)

My only thought is with the last lines about watchdog. it is asking you to deactivate MNI watchdog.

I do not know if removing watchdog will be necessary, but I assume it would be inconvenient to do so.

---

### Post by captlogic on 2007-06-15
> **bodhi.zazen said:**
> OMG ~ please consider posting long output like that as an attachment :)
My exact thought, right after I didn't click on the 'preview'.  #-o


My only thought is with the last lines about watchdog. it is asking you to deactivate MNI watchdog.

I do not know if removing watchdog will be necessary, but I assume it would be inconvenient to do so.

Here we go down the rabbit hole....

Thanks for helping.

---

### Post by j_macattack67 on 2007-06-28
Don't worry I keep having the same problem so you're not the only one.  I would like assistance as well.

---

### Post by bouktin on 2007-06-30
Hi, captlogic & all
I Have the same problem as yours (exactly)
the problem is : nmi_watchdog is activated, I'm searching the utility of it and how to set it off.

For the moment : 
[http://www.virtualbox.org/wiki/User_FAQ](http://www.virtualbox.org/wiki/User_FAQ) see "linux hosts" and "debian/ubuntu ..."

after somme search : 
[http://forums.gentoo.org/viewtopic-t-541806-highlight-virtualbox.html](http://forums.gentoo.org/viewtopic-t-541806-highlight-virtualbox.html)

I try it and come back

Edit : 
and it works : 

I have edited the **/boot/grub/menu.lst **: (and **BACKUP** it before)
add **nmi_watchdog=0** at the end of kernel line 
[INDENT]kernel          /vmlinuz-2.6.20-16-generic root=UUID=XXX ro quiet splash nmi_watchdog=0[/INDENT]
reboot
re-install vbox (from deb package or sources)

Edit 2 : more information about NMI : [http://www.linux-tutorial.info/modules.php?name=Tutorial&pageid=116](http://www.linux-tutorial.info/modules.php?name=Tutorial&pageid=116)

---

### Post by bodhi.zazen on 2007-06-30
Threads merged, same problem, same solution

---

### Post by jdonner on 2008-03-16
System: Gutsy 7.10

I'm not a total noob, but close. I only hope this can shed some light on the problem...

I was having a lot of the same problems as many of the posters as above. I used to run Virtualbox on Feisty without problems, but Gutsy has never worked. I would find that I could install and run the Virtualbox software and even create and configure machines, but whenever I would try to actually run a machine (and install an OS), the Vbox would crash. I would get the dreaded error of "/etc/init.d/vboxdrv" not installed, et cetera. 

Sometimes, I found that Virtualbox would even "lose" machines I had previously created the next time I ran the program; there wouldn't be anything in the machines list despite the fact that I had created a few different ones previously.

When I would try to start the vboxdrv service in the terminal:

sudo /etc/init.d/vboxdrv start

it would say that it doesn't exist (even though it is installed). When I would execute:

sudo /etc/init.d/vboxdrv setup

nothing would happen, it would just give me a syntax error and say that start and restart were the only valid commands it would accept.

I finally hit upon this after much hacking about... I ran as root, using gksudo, and executed the terminal commands: 

gsksudo cp /etc/init.d/vboxdrv /dev/

which copied the vboxdrv script into the /dev/ directory, since Virtualbox seems to keep having a problem when looking for it there.

That didn't work.

Okay, then, I decided to try yet again to install the Virtualbox package from scratch, using the terminal commands as mentioned in previous posts in this thread.

That didn't work, again. I then tried doing the same thing through Synaptic Package Manager, but had no luck.

But I then tried to run synaptic as root:

gksudo synaptic

and again selected all the Virtualbox packages and related items (I also included the server package as I've done before, but skipped the source code). 

Everything then installed perfectly, and voila! It is running correctly now. I can even install and run OSs now.

I don't know if the first copying of the script may have helped, but I included it anyway as it was part of my process.

So, maybe trying these tricks might help you if you've tried everything else.

Good luck!

Jay

---

### Post by omegamormegil on 2008-03-27
> **bodhi.zazen said:**
> Open a terminal,

Enter this command twice (I do not know why it does not work on the first try :twisted: )

```
sudo /etc/init.d/vboxdrv setup
```

If that fails, you need to install the kernel headers :

```
sudo aptitude install linux-headers-$(uname -r)
sudo /etc/init.d/vboxdrv setup
sudo /etc/init.d/vboxdrv setup
```

I was getting the error "VirtualBox kernel driver not installed." after upgrading to the Hardy beta, and this information got it working for me!  Thanks!

---

### Post by zyxyellowxyz on 2008-04-26
> **bodhi.zazen said:**
> Open a terminal,

Enter this command twice (I do not know why it does not work on the first try :twisted: )

```
sudo /etc/init.d/vboxdrv setup
```

If that fails, you need to install the kernel headers :

```
sudo aptitude install linux-headers-$(uname -r)
sudo /etc/init.d/vboxdrv setup
sudo /etc/init.d/vboxdrv setup
```

THANK YOU! it worked, but "setup" didn't. I would get this in  my konsole:
```
susan@susan-desktop:~$ sudo /etc/init.d/vboxdrv setup
 * Usage: /etc/init.d/vboxdrv {start|stop|restart|status}
```

After doing the second step (because the first one didn't work), I simply entered
```
sudo /etc/init.d/vboxdrv start
```
It opened it up, and is now working.

Thank you. I'm going to post a link back to this page for another person who was having the same issues as I was. :guitar:

---

### Post by tssge on 2008-05-11
Could you help me? i ran the sudo /etc/init.d/vboxdrv start and the sudo /etc/init.d/vboxdrv setup but all the terminal said was

tssge@Whitestar-II:~$ sudo /etc/init.d/vboxdrv setup
 * Usage: /etc/init.d/vboxdrv {start|stop|restart|status}
tssge@Whitestar-II:~$ sudo /etc/init.d/vboxdrv start
 * Starting VirtualBox kernel module vboxdrv                                    
 * No suitable module for running kernel found.
tssge@Whitestar-II:~$ sudo /etc/init.d/vboxdrv stop
 * Stopping VirtualBox kernel module vboxdrv                             [ OK ] 
tssge@Whitestar-II:~$ sudo /etc/init.d/vboxdrv start
 * Starting VirtualBox kernel module vboxdrv                                    
 * No suitable module for running kernel found.
tssge@Whitestar-II:~$ sudo /etc/init.d/vboxdrv restart
 * Stopping VirtualBox kernel module vboxdrv                             [ OK ] 
 * Starting VirtualBox kernel module vboxdrv                                    
 * No suitable module for running kernel found.
Please help me...

---

### Post by bodhi.zazen on 2008-05-11
Could be one of two problems :

1. You can try installing virtualbox-ose-modules

```
sudo apt-get virtualbox-ose-modules
```

[https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose-modules/+bug/210127](https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose-modules/+bug/210127)

2. Or a second bug with the OSE, with this you will need to either use an older kernel or remove the OSE and install the PUEL edition.

[https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose/+bug/179807](https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose/+bug/179807)

---

### Post by lingenfr on 2008-05-11
I upgraded to Hardy and needed to recompile my vbox. Unfortunately, vboxdrv setup failed because my / partition was full. I used gnuparted and fixed that and tried running

sudo /etc/init.d/vboxdrv setup again and got the following:

 * Stopping VirtualBox kernel module vboxdrv                             [ OK ]
 * Recompiling VirtualBox kernel module vboxdrv
 * Look at /var/log/vbox-install.log to find out what went wrong

vbox-install.log says:

make KBUILD_VERBOSE=1 -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/tmp/vbox.2 SRCROOT=/tmp/vbox.2 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
	echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";	\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\
	/bin/false)
mkdir -p /tmp/vbox.2/.tmp_versions ; rm -f /tmp/vbox.2/.tmp_versions/*
make -f scripts/Makefile.build obj=/tmp/vbox.2
  gcc -m32 -Wp,-MD,/tmp/vbox.2/linux/.SUPDrv-linux.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.3/include -D__KERNEL__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -maccumulate-outgoing-args -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -Iinclude/asm-x86/mach-default -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign   -I/lib/modules/2.6.24-16-generic/build/include  -I/tmp/vbox.2/ -I/tmp/vbox.2/include -I/tmp/vbox.2/r0drv/linux -D__KERNEL__ -DMODULE -DRT_OS_LINUX -DIN_RING0 -DIN_RT_R0 -DIN_SUP_R0 -DCONFIG_VBOXDRV_AS_MISC -DRT_ARCH_X86 -DVBOX_WITHOUT_IDT_PATCHING -DUSE_NEW_OS_INTERFACE_FOR_MM   -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(SUPDrv_linux)"  -D"KBUILD_MODNAME=KBUILD_STR(vboxdrv)" -c -o /tmp/vbox.2/linux/.tmp_SUPDrv-linux.o /tmp/vbox.2/linux/SUPDrv-linux.c
In file included from /tmp/vbox.2/include/iprt/types.h:72,
                 from /tmp/vbox.2/include/VBox/types.h:21,
                 from /tmp/vbox.2/SUPDRV.h:26,
                 from /tmp/vbox.2/linux/SUPDrv-linux.c:22:
include/linux/types.h:40: error: redefinition of typedef &#8216;uintptr_t&#8217;
/tmp/vbox.2/include/iprt/stdint.h:118: error: previous declaration of &#8216;uintptr_t&#8217; was here
In file included from include/linux/thread_info.h:33,
                 from include/linux/preempt.h:9,
                 from include/linux/spinlock.h:49,
                 from /tmp/vbox.2/SUPDRV.h:87,
                 from /tmp/vbox.2/linux/SUPDrv-linux.c:22:
include/linux/bitops.h:6:1: warning: "BIT" redefined
In file included from /tmp/vbox.2/include/VBox/cdefs.h:20,
                 from /tmp/vbox.2/SUPDRV.h:25,
                 from /tmp/vbox.2/linux/SUPDrv-linux.c:22:
/tmp/vbox.2/include/iprt/cdefs.h:1042:1: warning: this is the location of the previous definition
make[2]: *** [/tmp/vbox.2/linux/SUPDrv-linux.o] Error 1
make[1]: *** [_module_/tmp/vbox.2] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [vboxdrv] Error 2

Any ideas what I need to do?

---

### Post by tssge on 2008-05-12
I ran sudo apt-get virtualbox-ose-modules command and the reply from terminal was

tssge@Whitestar-II:~$ sudo apt-get virtualbox-ose-modules
[sudo] password for tssge: 
E: Virheellinen toiminto virtualbox-ose-modules

E:Virheellinen tominto ...  means E: Error action or something like that
 :(

---

### Post by nosarembo on 2008-05-12
@tssge - try using Synaptic to install "virtualbox-ose-modules-generic" instead. Worked for me!

---

### Post by dansan on 2008-05-15
Thanks! I got VB back by using plan B.

Now, it comes to light that usb mics are no longer working. I probably misread part of the Hardy setup. It asked whether to keep or update something about usb. Since I'd spent hours getting usb to work in Gutsy, I chose to keep what I had. Wrong choice?

How can I fix this?

Thanks,
Daniel






> **bodhi.zazen said:**
> Open a terminal,

Enter this command twice (I do not know why it does not work on the first try :twisted: )

```
sudo /etc/init.d/vboxdrv setup
```

If that fails, you need to install the kernel headers :

```
sudo aptitude install linux-headers-$(uname -r)
sudo /etc/init.d/vboxdrv setup
sudo /etc/init.d/vboxdrv setup
```

---

### Post by .adma on 2008-05-15
All, just follow the link at the bottom.  It is the best way to get this installed is to follow the link I have down at the bottom.  The only think I did different, is instead of running the command 

```
sudo dpkg -i xxxxxxx
```

I just opened the file from my desktop and it installed all of the dependencies properly.

[http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html](http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html)

**By the way, THIS ENABLES USB SUPPORT!!!**

---

### Post by tssge on 2008-05-24
Thank you very much ! I think that solved my problem, installing of the generic modules ! Thanks !:):)

---

### Post by liamsy on 2008-05-27
ok i have read though numerous amounts of threads on trying to install vbox, i cant find anyone with my problem.
i have ubuntu version 8.04 hardy this is my 5th install of it, i had vbox running in my last install of it, but i had to create a password for the root user to run it and it messed up everything else, i had to reinstall ubuntu because it turns out my cd drive is busted, and had to fix all my other original install problems anyway, when i try to run a vmachine it comes up couldnt run vbox kernel so i tryed all the command lines, reinstalling it and still no leeway i ahd to downgrade my linux kernel to get ubuntu working properly on my laptop (toshiba satellite L30) when i try to run the '/etc/init.d/vboxdrv setup' line it tells me auth failure, i have really run out off thing to do for this!! so please help!

---

### Post by .adma on 2008-05-27
This easiest thing I would do is to just reinstall use the following instructions:


[http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html](http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html)


Don't run the DPKG command though.  Just double click on the package to install it.  This should take care of everything..

---

### Post by Doby on 2008-06-20
this is what I get

tobin@Spartan:~$ sudo aptitude install linuix-headers-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "linuix-headers-2.6.22-15-generic"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done

---

### Post by Happy_Man on 2008-06-20
> **Doby said:**
> this is what I get

tobin@Spartan:~$ sudo aptitude install linuix-headers-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "linuix-headers-2.6.22-15-generic"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done
You spelled "linux" wrong...

---

