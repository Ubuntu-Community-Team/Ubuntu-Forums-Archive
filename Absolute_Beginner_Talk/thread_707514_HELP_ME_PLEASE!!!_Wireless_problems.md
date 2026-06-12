---
title: "HELP ME PLEASE!!! Wireless problems?"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by Adam.W on 2008-02-25
Hello
I have been trying to get my laptop to connect to a wireless network for over a week now and really don't know where to turn? I have a Lifebook B-2131 with xubuntu 7.10. This is my first Linux machine and I really like xubuntu but Im finding it hard to get the wireless to work. If the wireless worked the laptop would be perfect. 
I have been trying to connect with 3 diffrent devices. A PCMCIA card XI-330B, Belkin F5D7050 and a Netgear WG111v3 but with no joy. At one point the laptop detected the Belkin and the Belkin detected  routers that where in range but just wouldn't connect.:confused:

I am at a loss and loosing heart in xubuntu. I really like the OS but just can't seem to get this to work.:(

I have tried most of the threads on the forum but found a lot of them a bit hard to follow. I need it as simple as possible please.

Thanks

---

### Post by jan quark on 2008-02-25
let's try with the belkin 
as it seems you were close to a connection

but we need some input first

please run the following terminal commands and post the output
```

sudo lshw -C network
```

```
iwconfig
```

```
cat /etc/network/interfaces
```

---

### Post by Adam.W on 2008-02-26
This is what I got with the Belkin pluged in:

adam@laptopB2131:~$ sudo lshw -C network
[sudo] password for adam:
  *-network               
       description: Ethernet interface
       product: 82557/8/9 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: 10
       bus info: pci@0000:00:10.0
       logical name: eth0
       version: 08
       serial: 00:00:0e:d2:f8:d0
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI duplex=full firmware=N/A ip=192.168.254.50 latency=66 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
adam@laptopB2131:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

adam@laptopB2131:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

#iface eth0 inet dhcp

iface eth2 inet dhcp

auto eth2

iface eth0 inet dhcp

auto eth0
adam@laptopB2131:~$ 

What do you think?
at one point it detected the wireless.

Thanks for helping me out!

---

### Post by spiderbatdad on 2008-02-26
There doesn't seem to be any wireless card detected in the hardware list (sudo lshw -C net). There also appears to be an unnecessary extension (eth2). Ideally, you would show eth0 (wired) eth1 or wifi0 (wireless).
Do you show any drivers available in the Restricted Drivers Manager? What happens when you run ```
sudo apt-get update
```

---

### Post by Adam.W on 2008-02-26
adam@laptopB2131:~$ sudo apt-get update
[sudo] password for adam:
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy Release.gpg [191B]
Get: 2 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_GB        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_GB
Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/main Translation-en_GB [21.3kB]
Get: 4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/restricted Translation-en_GB [2395B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release
Get: 5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/universe Translation-en_GB [4405B]
Get: 6 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/multiverse Translation-en_GB [8133B]
Get: 7 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates Release.gpg [191B]        
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/main Translation-en_GB       
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/restricted Translation-en_GB 
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/universe Translation-en_GB   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_GB 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy Release                              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates Release                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/main Packages                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/multiverse Packages
Fetched 36.2kB in 17s (2026B/s)
Reading package lists... Done

Thanks for the quick reply.

---

### Post by spiderbatdad on 2008-02-26
Now could you post the result of ```
lspci
``` please?

---

### Post by Adam.W on 2008-02-26
adam@laptopB2131:~$ lspci
00:00.0 Host bridge: Intel Corporation 82440MX Host Bridge (rev 01)
00:00.1 Multimedia audio controller: Intel Corporation 82440MX AC'97 Audio Controller
00:07.0 Bridge: Intel Corporation 82440MX ISA Bridge (rev 01)
00:07.1 IDE interface: Intel Corporation 82440MX EIDE Controller
00:07.2 USB Controller: Intel Corporation 82440MX USB Universal Host Controller
00:07.3 Bridge: Intel Corporation 82440MX Power Management Controller
00:10.0 Ethernet controller: Intel Corporation 82557/8/9 Ethernet Pro 100 (rev 08)
00:11.0 Communication controller: Agere Systems F-1156IV WinModem (V90, 56KFlex) (rev 01)
00:13.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
00:14.0 VGA compatible controller: Trident Microsystems Cyber 9525 (rev 49)

Have I done somthing wrong?

---

### Post by spiderbatdad on 2008-02-26
Well...there doesn't appear to be a wireless card connected to this system.

---

### Post by Adam.W on 2008-02-26
Do you want me to plug in all my wireless devices and do something? only the belkin USB adapter is pluged in at the moment.

:confused:

---

### Post by spiderbatdad on 2008-02-26
Plug them in one at a time...I would think, and run lspci each time, looking for an indication of the new device.

---

### Post by Adam.W on 2008-02-26
Just tryed all three and they are all the same? I think I have done somthing because the lights on the USBs don't light up anymore. 

What can I do?

:confused:

---

### Post by spiderbatdad on 2008-02-26
```
lsusb
``` would show you any detected usb devices. Some usb devices don't get detected by hotplugging. That is they need to be plugged in when you start the computer, though not generally the case. I had some luck with a linksys pcmcia card and xubuntu some time ago on an older hp laptop. Not sure how to help right now. You might take a look at this: [http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux](http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux)
And google a little bit.

---

### Post by Adam.W on 2008-02-26
I have managed to find the belkin drivers and put them on to a disc can anybody tell me where to go from here? it is a exe file.

---

### Post by Arthur Archnix on 2008-02-26
Just to be clear, you have three wireless cards, and they all connect by usb? Is that right? I have a few questions for you:

1. These usb ports on your laptop, do they all work with other usb devices? Please test by grabbing a flash drive, or usb mouse, or usb keyboard, and plug this test device into each usb port on your computer. Do all three work? If not, post back here, if so then on to...

2. Please type out the full name (make, model) of each usb device and post it here. Also, let us know which one you think is the best - i.e., which one do you want to use? Before doing that though...

3. Open up a terminal and type these two commands:
```
dmesg
clear
```
Lots of output goes by. Ignore it, but leave the terminal open and open up a little text editor so that we can cut and paste the output into it. 

Now plug in your first usb device, then in the terminal type:
```
dmesg | tail
```
Unplug it and type the same (press up and the last command should appear)
```
dmesg | tail
```
Copy the output of those two commands to the text file, save that text file and name it after the usb wireless device. You can either paste the document here (use code or quote to wrap it) or else just attach the text file. Whichever is easier for you.

Now repeat for the remaining two. You may want to type clear again, to make it simpler. Just to give you an example, when I plug in the ipod, then type dmesg | tail here's what I get:
> arthur@archnix:~$ dmesg | tail
[ 3485.212000] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 3485.212000]  sdb: sdb1 sdb2
[ 3485.216000] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[ 3485.216000] sd 6:0:0:0: Attached scsi generic sg2 type 0
[ 3497.356000] usb 1-1: USB disconnect, address 3
[ 3572.060000] usb 1-1: new high speed USB device using ehci_hcd and address 4
[ 3572.192000] usb 1-1: configuration #1 chosen from 2 choices
[ 3572.192000] scsi7 : SCSI emulation for USB Mass Storage devices
[ 3572.192000] usb-storage: device found at 4
[ 3572.192000] usb-storage: waiting for device to settle before scanning


---

### Post by stalkingwolf on 2008-02-26
I have a wg111 v2 and it just works.  Here is a suggestion that might sound trite but is not meant to be.
It happened to me just the other night.  I could see my router connection, the system said i was connected, but no connection.  server not found.

Make sure that all connections are in fact connected.  I started checking the various plugs and connections.  when i got to my wireless router and tried the feed cable I got a resounding CLICK.

after that IT WORKS.

---

### Post by Adam.W on 2008-02-26
2 of them are USB and the other is a PCMCIA card.

I have a USB Belkin F5D7050v2, a USB Netgear WG111v3 and I have a PCMCIA card model XI-330B (The PCMCIA card being the preferred one to use).

I have a usb mouse plugged in and a external DVD rom drive and they both work fine in both USB ports.

I typed in the commands in to the terminal copyed
 the content into mousepad but I'm not sure how to attach the files to this post?

---

### Post by Arthur Archnix on 2008-02-26
Hit edit, go advanced, then by the smiley face is a paper clip icon to attach.

---

### Post by Adam.W on 2008-02-26
I tried that, didn´t want to work. I will just copy them into here.

adam@laptopB2131:~$ dmesg
[    0.000000] Linux version 2.6.22-14-386 (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 Tue Feb 12 07:12:19 UTC 2008 (Ubuntu 2.6.22-14.52-386)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ec400 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000007fe0000 (usable)
[    0.000000]  BIOS-e820: 0000000007fe0000 - 0000000007fefc00 (ACPI data)
[    0.000000]  BIOS-e820: 0000000007fefc00 - 0000000007ff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000007ff0000 - 0000000007ff1000 (reserved)
[    0.000000]  BIOS-e820: 0000000007ff1000 - 0000000008000000 (usable)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 128MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 32768) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    32768
[    0.000000]   HighMem     32768 ->    32768
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    32768
[    0.000000] On node 0 totalpages: 32768
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 224 pages used for memmap
[    0.000000]   Normal zone: 28448 pages, LIFO batch:7
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F68D0 checksum 0
[    0.000000] ACPI: RSDP 000F68D0, 0014 (r0 FUJ   )
[    0.000000] ACPI: RSDT 07FECB24, 0028 (r1 FUJ    CHIFFON   1070000 FUJ      1000)
[    0.000000] ACPI: FACP 07FEFB8C, 0074 (r1 FUJ    CHIFFON   1070000 FUJ      1000)
[    0.000000] ACPI: DSDT 07FECB4C, 3040 (r1 FUJ    CHIFFON   1070000 MSFT  1000007)
[    0.000000] ACPI: FACS 07FEFFC0, 0040
[    0.000000] ACPI: BIOS age (1999) fails cutoff (2000), acpi=force is required to enable ACPI
[    0.000000] ACPI: Disabling ACPI support
[    0.000000] Allocating PCI resources starting at 10000000 (gap: 08000000:f7f00000)
[    0.000000] Built 1 zonelists.  Total pages: 32512
[    0.000000] Kernel command line: root=UUID=bbca343b-d83d-48ee-835d-e0f0f31d43e7 ro quiet splash
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffd000 (01101000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 512 (order: 9, 2048 bytes)
[    0.000000] Detected 398.276 MHz processor.
[   19.765242] Console: colour VGA+ 80x25
[   19.765560] Dentry cache hash table entries: 16384 (order: 4, 65536 bytes)
[   19.765836] Inode-cache hash table entries: 8192 (order: 3, 32768 bytes)
[   19.781751] Memory: 119060k/131072k available (1929k kernel code, 11404k reserved, 876k data, 348k init, 0k highmem)
[   19.781802] virtual kernel memory layout:
[   19.781808]     fixmap  : 0xfffa8000 - 0xfffff000   ( 348 kB)
[   19.781815]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   19.781823]     vmalloc : 0xc8800000 - 0xff7fe000   ( 879 MB)
[   19.781830]     lowmem  : 0xc0000000 - 0xc8000000   ( 128 MB)
[   19.781837]       .init : 0xc03c0000 - 0xc0417000   ( 348 kB)
[   19.781844]       .data : 0xc02e2655 - 0xc03bda04   ( 876 kB)
[   19.781851]       .text : 0xc0100000 - 0xc02e2655   (1929 kB)
[   19.781867] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   19.782071] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   19.862110] Calibrating delay using timer specific routine.. 797.33 BogoMIPS (lpj=1594667)
[   19.862211] Security Framework v1.0.0 initialized
[   19.862249] SELinux:  Disabled at boot.
[   19.862278] Mount-cache hash table entries: 512
[   19.862691] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   19.862737] CPU: L1 I cache: 16K, L1 D cache: 16K
[   19.862750] CPU: L2 cache: 128K
[   19.862760] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[   19.862801] Compat vDSO mapped to ffffe000.
[   19.862846] CPU: Intel Celeron (Coppermine) stepping 01
[   19.862869] Checking 'hlt' instruction... OK.
[   19.880282] Early unpacking initramfs... done
[   21.380260] Booting paravirtualized kernel on bare hardware
[   21.380447] Time:  8:13:41  Date: 01/26/108
[   21.380557] NET: Registered protocol family 16
[   21.380973] EISA bus registered
[   21.384407] PCI: PCI BIOS revision 2.10 entry at 0xfd9be, last bus=1
[   21.384419] PCI: Using configuration type 1
[   21.384429] Setting up standard PCI resources
[   21.392643] ACPI: Interpreter disabled.
[   21.392662] Linux Plug and Play Support v0.97 (c) Adam Belay
[   21.392699] pnp: PnP ACPI: disabled
[   21.392715] PnPBIOS: Scanning system for PnP BIOS support...
[   21.392844] PnPBIOS: Found PnP BIOS installation structure at 0xc00f68f0
[   21.392860] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0x9219, dseg 0x400
[   21.401979] PnPBIOS: 17 nodes reported by PnP BIOS; 17 recorded by driver
[   21.402246] PCI: Probing PCI hardware
[   21.402297] PCI: Probing PCI hardware (bus 00)
[   21.402872] PCI quirk: region ff00-ff3f claimed by PIIX4 ACPI
[   21.402889] PCI quirk: region ff80-ff8f claimed by PIIX4 SMB
[   21.402905] PIIX4 devres C PIO at fd60-fd67
[   21.402918] PIIX4 devres G PIO at 0118-011f
[   21.402994] PCI: Firmware left 0000:00:10.0 e100 interrupts enabled, disabling
[   21.405769] PCI: Using IRQ router PIIX/ICH [8086/7198] at 0000:00:07.0
[   21.408461] NET: Registered protocol family 8
[   21.408473] NET: Registered protocol family 20
[   21.408861] pnp: 00:00: iomem range 0xfff00000-0xffffffff could not be reserved
[   21.408893] pnp: 00:01: iomem range 0x0-0x9ffff could not be reserved
[   21.408909] pnp: 00:01: iomem range 0xec000-0xfffff could not be reserved
[   21.408926] pnp: 00:01: iomem range 0x100000-0x7ffffff could not be reserved
[   21.408972] pnp: 00:0b: iomem range 0xcd000-0xcffff has been reserved
[   21.410129] Time: tsc clocksource has been installed.
[   21.410661] PCI: Bus 1, cardbus bridge: 0000:00:13.0
[   21.410676]   IO window: 00001c00-00001cff
[   21.410689]   IO window: 00002000-000020ff
[   21.410703]   PREFETCH window: 10000000-13ffffff
[   21.410717]   MEM window: 14000000-17ffffff
[   21.410754] PCI: setting IRQ 9 as level-triggered
[   21.410766] PCI: Found IRQ 9 for device 0000:00:13.0
[   21.410848] NET: Registered protocol family 2
[   21.450222] IP route cache hash table entries: 1024 (order: 0, 4096 bytes)
[   21.450367] TCP established hash table entries: 4096 (order: 3, 32768 bytes)
[   21.450546] TCP bind hash table entries: 4096 (order: 2, 16384 bytes)
[   21.450642] TCP: Hash tables configured (established 4096 bind 4096)
[   21.450654] TCP reno registered
[   21.462645] checking if image is initramfs... it is
[   24.305775] Freeing initrd memory: 6707k freed
[   24.306894] audit: initializing netlink socket (disabled)
[   24.306936] audit(1204013623.528:1): initialized
[   24.318310] VFS: Disk quotas dquot_6.5.1
[   24.318383] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   24.319115] io scheduler noop registered
[   24.319130] io scheduler anticipatory registered
[   24.319140] io scheduler deadline registered
[   24.319259] io scheduler cfq registered (default)
[   24.319326] Boot video device is 0000:00:14.0
[   24.319824] isapnp: Scanning for PnP cards...
[   24.673220] isapnp: No Plug & Play device found
[   24.853443] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   24.853623] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   24.855428] serial8250: ttyS3 at I/O 0x2e8 (irq = 3) is a 16550A
[   24.857301] 00:0e: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   24.861028] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   24.861668] input: Macintosh mouse button emulation as /class/input/input0
[   24.862106] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[   24.865661] serio: i8042 KBD port at 0x60,0x64 irq 1
[   24.865682] serio: i8042 AUX port at 0x60,0x64 irq 12
[   24.866587] mice: PS/2 mouse device common for all mice
[   24.867109] EISA: Probing bus 0 at eisa.0
[   24.867134] Cannot allocate resource for EISA slot 1
[   24.867147] Cannot allocate resource for EISA slot 2
[   24.867191] EISA: Detected 0 cards.
[   24.867558] TCP cubic registered
[   24.867614] NET: Registered protocol family 1
[   24.867706] Using IPI Shortcut mode
[   24.868044]   Magic number: 12:941:220
[   24.868127]   hash matches device ttyu4
[   24.869855] Freeing unused kernel memory: 348k freed
[   24.926304] input: AT Translated Set 2 keyboard as /class/input/input1
[   26.903960] fuse init (API version 7.8)
[   26.931854] Capability LSM initialized
[   27.001835] thermal: Unknown symbol acpi_processor_set_thermal_limit
[   29.538522] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k4-NAPI
[   29.538539] e100: Copyright(c) 1999-2006 Intel Corporation
[   29.538661] PCI: Found IRQ 9 for device 0000:00:10.0
[   29.538691] PCI: Sharing IRQ 9 with 0000:00:11.0
[   29.538707] PCI: Sharing IRQ 9 with 0000:00:14.0
[   29.561798] e100: eth0: e100_probe: addr 0xfe100000, irq 9, MAC addr 00:00:0E:D2:F8:D0
[   29.869378] SCSI subsystem initialized
[   29.913852] libata version 2.21 loaded.
[   29.938833] ata_piix 0000:00:07.1: version 2.11
[   29.939471] scsi0 : ata_piix
[   29.939671] scsi1 : ata_piix
[   29.939802] ata1: PATA max UDMA/33 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011480 irq 14
[   29.939822] ata2: PATA max UDMA/33 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011488 irq 15
[   30.039025] usbcore: registered new interface driver usbfs
[   30.039134] usbcore: registered new interface driver hub
[   30.039250] usbcore: registered new device driver usb
[   30.045408] USB Universal Host Controller Interface driver v3.0
[   30.114049] ata1.00: ATA-4: FUJITSU MHH2064AT, BC16, max UDMA/33
[   30.114070] ata1.00: 11733120 sectors, multi 16: LBA 
[   30.158142] ata1.00: configured for UDMA/33
[   30.158302] ata2: port disabled. ignoring.
[   30.166436] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHH2064A BC16 PQ: 0 ANSI: 5
[   30.167630] PCI: Enabling device 0000:00:07.2 (0000 -> 0001)
[   30.167658] PCI: Found IRQ 9 for device 0000:00:07.2
[   30.167712] uhci_hcd 0000:00:07.2: UHCI Host Controller
[   30.168285] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[   30.168348] uhci_hcd 0000:00:07.2: irq 9, io base 0x000014a0
[   30.168903] usb usb1: configuration #1 chosen from 1 choice
[   30.169035] hub 1-0:1.0: USB hub found
[   30.169074] hub 1-0:1.0: 2 ports detected
[   30.412905] Floppy drive(s): fd0 is 1.44M
[   30.510287] usb 1-2: new low speed USB device using uhci_hcd and address 2
[   30.682133] FDC 0 is a post-1991 82077
[   30.683794] usb 1-2: configuration #1 chosen from 1 choice
[   30.919505] usbcore: registered new interface driver hiddev
[   30.966739] input: Dell Dell USB Mouse as /class/input/input2
[   30.967670] input: USB HID v1.10 Mouse [Dell Dell USB Mouse] on usb-0000:00:07.2-2
[   30.967740] usbcore: registered new interface driver usbhid
[   30.967757] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   31.002378] sd 0:0:0:0: [sda] 11733120 512-byte hardware sectors (6007 MB)
[   31.006336] sd 0:0:0:0: [sda] Write Protect is off
[   31.006364] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   31.006916] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   31.007169] sd 0:0:0:0: [sda] 11733120 512-byte hardware sectors (6007 MB)
[   31.007218] sd 0:0:0:0: [sda] Write Protect is off
[   31.007232] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   31.007302] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   31.007326]  sda: sda1 sda2 < sda5 >
[   31.119515] sd 0:0:0:0: [sda] Attached SCSI disk
[   31.143812] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   31.837045] Attempting manual resume
[   31.837061] swsusp: Resume From Partition 8:5
[   31.837071] PM: Checking swsusp image.
[   31.869009] PM: Resume from disk failed.
[   32.010350] kjournald starting.  Commit interval 5 seconds
[   32.010408] EXT3-fs: mounted filesystem with ordered data mode.
[   43.826527] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[   45.608025] NET: Registered protocol family 17
[   49.100647] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[   51.913123] Yenta: CardBus bridge found at 0000:00:13.0 [10cf:10c6]
[   51.913158] Yenta: adjusting diagnostic: 41 -> 61
[   51.913171] Yenta: Enabling burst memory read transactions
[   51.913184] Yenta: Using CSCINT to route CSC interrupts to PCI
[   51.913195] Yenta: Routing CardBus interrupts to PCI
[   51.913210] Yenta TI: socket 0000:00:13.0, mfunc 0x01d11622, devctl 0x46
[   52.005676] input: PC Speaker as /class/input/input3
[   52.064790] input: PS/2 Touchpad as /class/input/input4
[   52.163110] Yenta: ISA IRQ mask 0x0cb8, PCI irq 9
[   52.163126] Socket status: 30000010
[   52.282328] input: LBPS/2 Fujitsu Lifebook TouchScreen as /class/input/input5
[   52.798449] pccard: PCMCIA card inserted into slot 0
[   53.207702] Real Time Clock Driver v1.12ac
[   53.253051] parport_pc 00:13: reported by Plug and Play BIOS
[   53.253109] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   53.574672] irda_init()
[   53.574738] NET: Registered protocol family 23
[   53.626709] found SMC SuperIO Chip (devid=0x28 rev=01 base=0x03f0): FDC37N769
[   53.626744] smsc_superio_flat(): fir: 0x118, sir: 0x2e8, dma: 03, irq: 3, mode: 0x0e
[   53.626764] smsc_ircc_present: can't get sir_base of 0x2e8
[   55.679626] cs: IO port probe 0x100-0x3af: excluding 0x118-0x11f
[   55.680625] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   55.681119] cs: IO port probe 0x820-0x8ff: clean.
[   55.681546] cs: IO port probe 0xc00-0xcf7: clean.
[   55.682339] cs: IO port probe 0xa00-0xaff: clean.
[   55.683052] cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   55.693536] pcmcia: registering new device pcmcia0.0
[   55.830936] PCI: Found IRQ 9 for device 0000:00:00.1
[   55.831188] PCI: Setting latency timer of device 0000:00:00.1 to 64
[   56.154404] intel8x0_measure_ac97_clock: measured 55928 usecs
[   56.154425] intel8x0: clocking to 48000
[   57.076106] loop: module loaded
[   57.150127] lp0: using parport0 (interrupt-driven).
[   57.381227] Adding 305192k swap on /dev/sda5.  Priority:-1 extents:1 across:305192k
[  126.338815] pccard: card ejected from slot 0
[  183.255949] EXT3 FS on sda1, internal journal
[  193.586363] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
[  193.586791] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
[  193.587674] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
[  193.588226] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
[  198.023357] ppdev: user-space parallel port driver
[  200.314338] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  201.720439] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
[  202.159416] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[  202.160394] NFSD: starting 90-second grace period
[  203.143557] hub 1-0:1.0: over-current change on port 1
[  203.487540] usb 1-1: new full speed USB device using uhci_hcd and address 3
[  203.819248] usb 1-1: configuration #1 chosen from 1 choice
[  205.090018] Capability LSM initialized
[  205.845747] Bluetooth: Core ver 2.11
[  205.846128] NET: Registered protocol family 31
[  205.846142] Bluetooth: HCI device and connection manager initialized
[  205.846156] Bluetooth: HCI socket layer initialized
[  205.972366] Bluetooth: L2CAP ver 2.8
[  205.972388] Bluetooth: L2CAP socket layer initialized
[  206.024041] Bluetooth: RFCOMM socket layer initialized
[  206.024363] Bluetooth: RFCOMM TTY layer initialized
[  206.024377] Bluetooth: RFCOMM ver 1.8
[  357.769088] NET: Registered protocol family 10
[  357.769613] lo: Disabled Privacy Extensions
[  368.180755] eth0: no IPv6 routers present
[ 1005.442837] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
[ 1005.442860] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[ 1005.442877] pcmcia: see [http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html](http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html) for details.
[ 1094.978320] usb 1-2: USB disconnect, address 2
[ 1101.530439] hub 1-0:1.0: over-current change on port 2
[ 1101.874331] usb 1-2: new full speed USB device using uhci_hcd and address 4
[ 1102.045590] usb 1-2: configuration #1 chosen from 1 choice
[ 1103.634335] pccard: PCMCIA card inserted into slot 0
[ 1103.634693] pcmcia: registering new device pcmcia0.0
[ 1172.594898] usb 1-2: USB disconnect, address 4
[ 1173.842884] usb 1-2: new full speed USB device using uhci_hcd and address 5
[ 1174.015006] usb 1-2: configuration #1 chosen from 1 choice
[ 1190.739039] usb 1-2: USB disconnect, address 5
[ 1192.573238] pccard: card ejected from slot 0
[ 1195.515037] usb 1-2: new low speed USB device using uhci_hcd and address 6
[ 1195.689257] usb 1-2: configuration #1 chosen from 1 choice
[ 1195.708347] input: Dell Dell USB Mouse as /class/input/input6
[ 1195.708545] input: USB HID v1.10 Mouse [Dell Dell USB Mouse] on usb-0000:00:07.2-2
[ 6701.128682] pccard: PCMCIA card inserted into slot 0
[ 6701.129047] pcmcia: registering new device pcmcia0.0
[ 6706.304791] usb 1-2: USB disconnect, address 6
[ 6710.084792] hub 1-0:1.0: over-current change on port 2
[ 6710.428772] usb 1-2: new full speed USB device using uhci_hcd and address 7
[ 6710.599226] usb 1-2: configuration #1 chosen from 1 choice
[ 6819.201642] usb 1-2: USB disconnect, address 7
[ 6825.489632] usb 1-2: new low speed USB device using uhci_hcd and address 8
[ 6825.663263] usb 1-2: configuration #1 chosen from 1 choice
[ 6825.682337] input: Dell Dell USB Mouse as /class/input/input7
[ 6825.682532] input: USB HID v1.10 Mouse [Dell Dell USB Mouse] on usb-0000:00:07.2-2
[ 7000.894999] usb 1-1: USB disconnect, address 3
[ 7109.573907] pccard: card ejected from slot 0
[ 7111.775836] hub 1-0:1.0: over-current change on port 1
[ 7112.119800] usb 1-1: new full speed USB device using uhci_hcd and address 9
[ 7112.286151] usb 1-1: configuration #1 chosen from 1 choice
[ 7432.070258] usb 1-1: USB disconnect, address 9
[ 7436.354285] hub 1-0:1.0: over-current change on port 1
[ 7436.698257] usb 1-1: new full speed USB device using uhci_hcd and address 10
[ 7436.867857] usb 1-1: configuration #1 chosen from 1 choice
[ 7441.142330] usb 1-1: USB disconnect, address 10
[ 7443.914342] hub 1-0:1.0: over-current change on port 1
[ 7444.258312] usb 1-1: new full speed USB device using uhci_hcd and address 11
[ 7444.588143] usb 1-1: configuration #1 chosen from 1 choice
[ 7451.978407] usb 1-1: USB disconnect, address 11
[10179.143055] hub 1-0:1.0: over-current change on port 1
[10179.487030] usb 1-1: new full speed USB device using uhci_hcd and address 12
[10179.813464] usb 1-1: configuration #1 chosen from 1 choice
[10505.485840] usb 1-1: USB disconnect, address 12
[10911.208574] hub 1-0:1.0: over-current change on port 1
[10911.552548] usb 1-1: new full speed USB device using uhci_hcd and address 13
[10911.884831] usb 1-1: configuration #1 chosen from 1 choice
[11170.518543] usb 1-1: USB disconnect, address 13
[11211.846843] hub 1-0:1.0: over-current change on port 1
[11213.598835] usb 1-1: new full speed USB device using uhci_hcd and address 14
[11213.752414] usb 1-1: configuration #1 chosen from 1 choice
[11215.594667] usbcore: registered new interface driver libusual
[11216.396414] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[11216.396756] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[11216.671756] Initializing USB Mass Storage driver...
[11216.678292] scsi2 : SCSI emulation for USB Mass Storage devices
[11216.688350] usb-storage: device found at 14
[11216.688368] usb-storage: waiting for device to settle before scanning
[11216.688942] usbcore: registered new interface driver usb-storage
[11216.689235] USB Mass Storage support registered.
[11221.688432] usb-storage: device scan complete
[11221.693494] scsi 2:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4243N A102 PQ: 0 ANSI: 0
[11221.696105] scsi 2:0:0:0: Attached scsi generic sg1 type 5
[11221.877335] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[11221.877359] Uniform CD-ROM driver Revision: 3.20
[11221.878925] sr 2:0:0:0: Attached scsi CD-ROM sr0
[11715.542723] usb 1-1: USB disconnect, address 14
[12174.494127] hub 1-0:1.0: over-current change on port 1
[12176.246109] usb 1-1: new full speed USB device using uhci_hcd and address 15
[12176.399762] usb 1-1: configuration #1 chosen from 1 choice
[12176.403092] scsi3 : SCSI emulation for USB Mass Storage devices
[12176.403727] usb-storage: device found at 15
[12176.403741] usb-storage: waiting for device to settle before scanning
[12181.403449] usb-storage: device scan complete
[12181.406530] scsi 3:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4243N A102 PQ: 0 ANSI: 0
[12181.498390] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[12181.498605] sr 3:0:0:0: Attached scsi CD-ROM sr0
[12181.498765] sr 3:0:0:0: Attached scsi generic sg1 type 5
[12192.857932] ISO 9660 Extensions: Microsoft Joliet Level 3
[12192.894000] ISOFS: changing to secondary root
[12242.534643] usb 1-2: USB disconnect, address 8
[12250.598704] hub 1-0:1.0: over-current change on port 2
[12250.942693] usb 1-2: new full speed USB device using uhci_hcd and address 16
[12251.274549] usb 1-2: configuration #1 chosen from 1 choice
[12383.655975] usb 1-1: USB disconnect, address 15
[12386.427737] hub 1-0:1.0: over-current change on port 1
[12386.771807] usb 1-1: new full speed USB device using uhci_hcd and address 17
[12386.919156] usb 1-1: configuration #1 chosen from 1 choice
[12386.921041] hub 1-1:1.0: USB hub found
[12386.923888] hub 1-1:1.0: 4 ports detected
[12392.223802] hub 1-0:1.0: port 1 disabled by hub (EMI?), re-enabling...
[12392.223826] hub 1-0:1.0: over-current change on port 1
[12392.327748] usb 1-1: USB disconnect, address 17
[12392.439779] usb 1-1: new full speed USB device using uhci_hcd and address 18
[12392.587007] usb 1-1: configuration #1 chosen from 1 choice
[12392.588810] hub 1-1:1.0: USB hub found
[12392.591667] hub 1-1:1.0: 4 ports detected
[12393.981343] usb 1-1.4: new full speed USB device using uhci_hcd and address 19
[12394.112630] usb 1-1.4: configuration #1 chosen from 1 choice
[12394.115949] scsi4 : SCSI emulation for USB Mass Storage devices
[12394.116582] usb-storage: device found at 19
[12394.116596] usb-storage: waiting for device to settle before scanning
[12396.160876] usb 1-1.3: new low speed USB device using uhci_hcd and address 20
[12396.314144] usb 1-1.3: configuration #1 chosen from 1 choice
[12396.333278] input: Dell Dell USB Mouse as /class/input/input8
[12396.333474] input: USB HID v1.10 Mouse [Dell Dell USB Mouse] on usb-0000:00:07.2-1.3
[12399.117299] usb-storage: device scan complete
[12399.122345] scsi 4:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4243N A102 PQ: 0 ANSI: 0
[12399.155240] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[12399.155475] sr 4:0:0:0: Attached scsi CD-ROM sr0
[12399.155633] sr 4:0:0:0: Attached scsi generic sg1 type 5
[12813.822977] usb 1-2: USB disconnect, address 16
[12837.499119] usb 1-2: new full speed USB device using uhci_hcd and address 21
[12837.885483] usb 1-2: configuration #1 chosen from 1 choice
[13567.084628] pccard: PCMCIA card inserted into slot 0
[13567.084988] pcmcia: registering new device pcmcia0.0
adam@laptopB2131:~$ clear

adam@laptopB2131:~$ dmesg
[    0.000000] Linux version 2.6.22-14-386 (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 Tue Feb 12 07:12:19 UTC 2008 (Ubuntu 2.6.22-14.52-386)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ec400 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000007fe0000 (usable)
[    0.000000]  BIOS-e820: 0000000007fe0000 - 0000000007fefc00 (ACPI data)
[    0.000000]  BIOS-e820: 0000000007fefc00 - 0000000007ff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000007ff0000 - 0000000007ff1000 (reserved)
[    0.000000]  BIOS-e820: 0000000007ff1000 - 0000000008000000 (usable)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 128MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 32768) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    32768
[    0.000000]   HighMem     32768 ->    32768
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    32768
[    0.000000] On node 0 totalpages: 32768
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 224 pages used for memmap
[    0.000000]   Normal zone: 28448 pages, LIFO batch:7
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F68D0 checksum 0
[    0.000000] ACPI: RSDP 000F68D0, 0014 (r0 FUJ   )
[    0.000000] ACPI: RSDT 07FECB24, 0028 (r1 FUJ    CHIFFON   1070000 FUJ      1000)
[    0.000000] ACPI: FACP 07FEFB8C, 0074 (r1 FUJ    CHIFFON   1070000 FUJ      1000)
[    0.000000] ACPI: DSDT 07FECB4C, 3040 (r1 FUJ    CHIFFON   1070000 MSFT  1000007)
[    0.000000] ACPI: FACS 07FEFFC0, 0040
[    0.000000] ACPI: BIOS age (1999) fails cutoff (2000), acpi=force is required to enable ACPI
[    0.000000] ACPI: Disabling ACPI support
[    0.000000] Allocating PCI resources starting at 10000000 (gap: 08000000:f7f00000)
[    0.000000] Built 1 zonelists.  Total pages: 32512
[    0.000000] Kernel command line: root=UUID=bbca343b-d83d-48ee-835d-e0f0f31d43e7 ro quiet splash
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffd000 (01101000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 512 (order: 9, 2048 bytes)
[    0.000000] Detected 398.276 MHz processor.
[   19.765242] Console: colour VGA+ 80x25
[   19.765560] Dentry cache hash table entries: 16384 (order: 4, 65536 bytes)
[   19.765836] Inode-cache hash table entries: 8192 (order: 3, 32768 bytes)
[   19.781751] Memory: 119060k/131072k available (1929k kernel code, 11404k reserved, 876k data, 348k init, 0k highmem)
[   19.781802] virtual kernel memory layout:
[   19.781808]     fixmap  : 0xfffa8000 - 0xfffff000   ( 348 kB)
[   19.781815]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   19.781823]     vmalloc : 0xc8800000 - 0xff7fe000   ( 879 MB)
[   19.781830]     lowmem  : 0xc0000000 - 0xc8000000   ( 128 MB)
[   19.781837]       .init : 0xc03c0000 - 0xc0417000   ( 348 kB)
[   19.781844]       .data : 0xc02e2655 - 0xc03bda04   ( 876 kB)
[   19.781851]       .text : 0xc0100000 - 0xc02e2655   (1929 kB)
[   19.781867] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   19.782071] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   19.862110] Calibrating delay using timer specific routine.. 797.33 BogoMIPS (lpj=1594667)
[   19.862211] Security Framework v1.0.0 initialized
[   19.862249] SELinux:  Disabled at boot.
[   19.862278] Mount-cache hash table entries: 512
[   19.862691] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   19.862737] CPU: L1 I cache: 16K, L1 D cache: 16K
[   19.862750] CPU: L2 cache: 128K
[   19.862760] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[   19.862801] Compat vDSO mapped to ffffe000.
[   19.862846] CPU: Intel Celeron (Coppermine) stepping 01
[   19.862869] Checking 'hlt' instruction... OK.
[   19.880282] Early unpacking initramfs... done
[   21.380260] Booting paravirtualized kernel on bare hardware
[   21.380447] Time:  8:13:41  Date: 01/26/108
[   21.380557] NET: Registered protocol family 16
[   21.380973] EISA bus registered
[   21.384407] PCI: PCI BIOS revision 2.10 entry at 0xfd9be, last bus=1
[   21.384419] PCI: Using configuration type 1
[   21.384429] Setting up standard PCI resources
[   21.392643] ACPI: Interpreter disabled.
[   21.392662] Linux Plug and Play Support v0.97 (c) Adam Belay
[   21.392699] pnp: PnP ACPI: disabled
[   21.392715] PnPBIOS: Scanning system for PnP BIOS support...
[   21.392844] PnPBIOS: Found PnP BIOS installation structure at 0xc00f68f0
[   21.392860] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0x9219, dseg 0x400
[   21.401979] PnPBIOS: 17 nodes reported by PnP BIOS; 17 recorded by driver
[   21.402246] PCI: Probing PCI hardware
[   21.402297] PCI: Probing PCI hardware (bus 00)
[   21.402872] PCI quirk: region ff00-ff3f claimed by PIIX4 ACPI
[   21.402889] PCI quirk: region ff80-ff8f claimed by PIIX4 SMB
[   21.402905] PIIX4 devres C PIO at fd60-fd67
[   21.402918] PIIX4 devres G PIO at 0118-011f
[   21.402994] PCI: Firmware left 0000:00:10.0 e100 interrupts enabled, disabling
[   21.405769] PCI: Using IRQ router PIIX/ICH [8086/7198] at 0000:00:07.0
[   21.408461] NET: Registered protocol family 8
[   21.408473] NET: Registered protocol family 20
[   21.408861] pnp: 00:00: iomem range 0xfff00000-0xffffffff could not be reserved
[   21.408893] pnp: 00:01: iomem range 0x0-0x9ffff could not be reserved
[   21.408909] pnp: 00:01: iomem range 0xec000-0xfffff could not be reserved
[   21.408926] pnp: 00:01: iomem range 0x100000-0x7ffffff could not be reserved
[   21.408972] pnp: 00:0b: iomem range 0xcd000-0xcffff has been reserved
[   21.410129] Time: tsc clocksource has been installed.
[   21.410661] PCI: Bus 1, cardbus bridge: 0000:00:13.0
[   21.410676]   IO window: 00001c00-00001cff
[   21.410689]   IO window: 00002000-000020ff
[   21.410703]   PREFETCH window: 10000000-13ffffff
[   21.410717]   MEM window: 14000000-17ffffff
[   21.410754] PCI: setting IRQ 9 as level-triggered
[   21.410766] PCI: Found IRQ 9 for device 0000:00:13.0
[   21.410848] NET: Registered protocol family 2
[   21.450222] IP route cache hash table entries: 1024 (order: 0, 4096 bytes)
[   21.450367] TCP established hash table entries: 4096 (order: 3, 32768 bytes)
[   21.450546] TCP bind hash table entries: 4096 (order: 2, 16384 bytes)
[   21.450642] TCP: Hash tables configured (established 4096 bind 4096)
[   21.450654] TCP reno registered
[   21.462645] checking if image is initramfs... it is
[   24.305775] Freeing initrd memory: 6707k freed
[   24.306894] audit: initializing netlink socket (disabled)
[   24.306936] audit(1204013623.528:1): initialized
[   24.318310] VFS: Disk quotas dquot_6.5.1
[   24.318383] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   24.319115] io scheduler noop registered
[   24.319130] io scheduler anticipatory registered
[   24.319140] io scheduler deadline registered
[   24.319259] io scheduler cfq registered (default)
[   24.319326] Boot video device is 0000:00:14.0
[   24.319824] isapnp: Scanning for PnP cards...
[   24.673220] isapnp: No Plug & Play device found
[   24.853443] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   24.853623] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   24.855428] serial8250: ttyS3 at I/O 0x2e8 (irq = 3) is a 16550A
[   24.857301] 00:0e: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   24.861028] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   24.861668] input: Macintosh mouse button emulation as /class/input/input0
[   24.862106] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[   24.865661] serio: i8042 KBD port at 0x60,0x64 irq 1
[   24.865682] serio: i8042 AUX port at 0x60,0x64 irq 12
[   24.866587] mice: PS/2 mouse device common for all mice
[   24.867109] EISA: Probing bus 0 at eisa.0
[   24.867134] Cannot allocate resource for EISA slot 1
[   24.867147] Cannot allocate resource for EISA slot 2
[   24.867191] EISA: Detected 0 cards.
[   24.867558] TCP cubic registered
[   24.867614] NET: Registered protocol family 1
[   24.867706] Using IPI Shortcut mode
[   24.868044]   Magic number: 12:941:220
[   24.868127]   hash matches device ttyu4
[   24.869855] Freeing unused kernel memory: 348k freed
[   24.926304] input: AT Translated Set 2 keyboard as /class/input/input1
[   26.903960] fuse init (API version 7.8)
[   26.931854] Capability LSM initialized
[   27.001835] thermal: Unknown symbol acpi_processor_set_thermal_limit
[   29.538522] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k4-NAPI
[   29.538539] e100: Copyright(c) 1999-2006 Intel Corporation
[   29.538661] PCI: Found IRQ 9 for device 0000:00:10.0
[   29.538691] PCI: Sharing IRQ 9 with 0000:00:11.0
[   29.538707] PCI: Sharing IRQ 9 with 0000:00:14.0
[   29.561798] e100: eth0: e100_probe: addr 0xfe100000, irq 9, MAC addr 00:00:0E:D2:F8:D0
[   29.869378] SCSI subsystem initialized
[   29.913852] libata version 2.21 loaded.
[   29.938833] ata_piix 0000:00:07.1: version 2.11
[   29.939471] scsi0 : ata_piix
[   29.939671] scsi1 : ata_piix
[   29.939802] ata1: PATA max UDMA/33 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011480 irq 14
[   29.939822] ata2: PATA max UDMA/33 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011488 irq 15
[   30.039025] usbcore: registered new interface driver usbfs
[   30.039134] usbcore: registered new interface driver hub
[   30.039250] usbcore: registered new device driver usb
[   30.045408] USB Universal Host Controller Interface driver v3.0
[   30.114049] ata1.00: ATA-4: FUJITSU MHH2064AT, BC16, max UDMA/33
[   30.114070] ata1.00: 11733120 sectors, multi 16: LBA 
[   30.158142] ata1.00: configured for UDMA/33
[   30.158302] ata2: port disabled. ignoring.
[   30.166436] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHH2064A BC16 PQ: 0 ANSI: 5
[   30.167630] PCI: Enabling device 0000:00:07.2 (0000 -> 0001)
[   30.167658] PCI: Found IRQ 9 for device 0000:00:07.2
[   30.167712] uhci_hcd 0000:00:07.2: UHCI Host Controller
[   30.168285] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[   30.168348] uhci_hcd 0000:00:07.2: irq 9, io base 0x000014a0
[   30.168903] usb usb1: configuration #1 chosen from 1 choice
[   30.169035] hub 1-0:1.0: USB hub found
[   30.169074] hub 1-0:1.0: 2 ports detected
[   30.412905] Floppy drive(s): fd0 is 1.44M
[   30.510287] usb 1-2: new low speed USB device using uhci_hcd and address 2
[   30.682133] FDC 0 is a post-1991 82077
[   30.683794] usb 1-2: configuration #1 chosen from 1 choice
[   30.919505] usbcore: registered new interface driver hiddev
[   30.966739] input: Dell Dell USB Mouse as /class/input/input2
[   30.967670] input: USB HID v1.10 Mouse [Dell Dell USB Mouse] on usb-0000:00:07.2-2
[   30.967740] usbcore: registered new interface driver usbhid
[   30.967757] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   31.002378] sd 0:0:0:0: [sda] 11733120 512-byte hardware sectors (6007 MB)
[   31.006336] sd 0:0:0:0: [sda] Write Protect is off
[   31.006364] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   31.006916] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   31.007169] sd 0:0:0:0: [sda] 11733120 512-byte hardware sectors (6007 MB)
[   31.007218] sd 0:0:0:0: [sda] Write Protect is off
[   31.007232] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   31.007302] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   31.007326]  sda: sda1 sda2 < sda5 >
[   31.119515] sd 0:0:0:0: [sda] Attached SCSI disk
[   31.143812] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   31.837045] Attempting manual resume
[   31.837061] swsusp: Resume From Partition 8:5
[   31.837071] PM: Checking swsusp image.
[   31.869009] PM: Resume from disk failed.
[   32.010350] kjournald starting.  Commit interval 5 seconds
[   32.010408] EXT3-fs: mounted filesystem with ordered data mode.
[   43.826527] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[   45.608025] NET: Registered protocol family 17
[   49.100647] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[   51.913123] Yenta: CardBus bridge found at 0000:00:13.0 [10cf:10c6]
[   51.913158] Yenta: adjusting diagnostic: 41 -> 61
[   51.913171] Yenta: Enabling burst memory read transactions
[   51.913184] Yenta: Using CSCINT to route CSC interrupts to PCI
[   51.913195] Yenta: Routing CardBus interrupts to PCI
[   51.913210] Yenta TI: socket 0000:00:13.0, mfunc 0x01d11622, devctl 0x46
[   52.005676] input: PC Speaker as /class/input/input3
[   52.064790] input: PS/2 Touchpad as /class/input/input4
[   52.163110] Yenta: ISA IRQ mask 0x0cb8, PCI irq 9
[   52.163126] Socket status: 30000010
[   52.282328] input: LBPS/2 Fujitsu Lifebook TouchScreen as /class/input/input5
[   52.798449] pccard: PCMCIA card inserted into slot 0
[   53.207702] Real Time Clock Driver v1.12ac
[   53.253051] parport_pc 00:13: reported by Plug and Play BIOS
[   53.253109] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   53.574672] irda_init()
[   53.574738] NET: Registered protocol family 23
[   53.626709] found SMC SuperIO Chip (devid=0x28 rev=01 base=0x03f0): FDC37N769
[   53.626744] smsc_superio_flat(): fir: 0x118, sir: 0x2e8, dma: 03, irq: 3, mode: 0x0e
[   53.626764] smsc_ircc_present: can't get sir_base of 0x2e8
[   55.679626] cs: IO port probe 0x100-0x3af: excluding 0x118-0x11f
[   55.680625] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   55.681119] cs: IO port probe 0x820-0x8ff: clean.
[   55.681546] cs: IO port probe 0xc00-0xcf7: clean.
[   55.682339] cs: IO port probe 0xa00-0xaff: clean.
[   55.683052] cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   55.693536] pcmcia: registering new device pcmcia0.0
[   55.830936] PCI: Found IRQ 9 for device 0000:00:00.1
[   55.831188] PCI: Setting latency timer of device 0000:00:00.1 to 64
[   56.154404] intel8x0_measure_ac97_clock: measured 55928 usecs
[   56.154425] intel8x0: clocking to 48000
[   57.076106] loop: module loaded
[   57.150127] lp0: using parport0 (interrupt-driven).
[   57.381227] Adding 305192k swap on /dev/sda5.  Priority:-1 extents:1 across:305192k
[  126.338815] pccard: card ejected from slot 0
[  183.255949] EXT3 FS on sda1, internal journal
[  193.586363] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
[  193.586791] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
[  193.587674] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
[  193.588226] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
[  198.023357] ppdev: user-space parallel port driver
[  200.314338] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  201.720439] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
[  202.159416] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[  202.160394] NFSD: starting 90-second grace period
[  203.143557] hub 1-0:1.0: over-current change on port 1
[  203.487540] usb 1-1: new full speed USB device using uhci_hcd and address 3
[  203.819248] usb 1-1: configuration #1 chosen from 1 choice
[  205.090018] Capability LSM initialized
[  205.845747] Bluetooth: Core ver 2.11
[  205.846128] NET: Registered protocol family 31
[  205.846142] Bluetooth: HCI device and connection manager initialized
[  205.846156] Bluetooth: HCI socket layer initialized
[  205.972366] Bluetooth: L2CAP ver 2.8
[  205.972388] Bluetooth: L2CAP socket layer initialized
[  206.024041] Bluetooth: RFCOMM socket layer initialized
[  206.024363] Bluetooth: RFCOMM TTY layer initialized
[  206.024377] Bluetooth: RFCOMM ver 1.8
[  357.769088] NET: Registered protocol family 10
[  357.769613] lo: Disabled Privacy Extensions
[  368.180755] eth0: no IPv6 routers present
[ 1005.442837] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
[ 1005.442860] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[ 1005.442877] pcmcia: see [http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html](http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html) for details.
[ 1094.978320] usb 1-2: USB disconnect, address 2
[ 1101.530439] hub 1-0:1.0: over-current change on port 2
[ 1101.874331] usb 1-2: new full speed USB device using uhci_hcd and address 4
[ 1102.045590] usb 1-2: configuration #1 chosen from 1 choice
[ 1103.634335] pccard: PCMCIA card inserted into slot 0
[ 1103.634693] pcmcia: registering new device pcmcia0.0
[ 1172.594898] usb 1-2: USB disconnect, address 4
[ 1173.842884] usb 1-2: new full speed USB device using uhci_hcd and address 5
[ 1174.015006] usb 1-2: configuration #1 chosen from 1 choice
[ 1190.739039] usb 1-2: USB disconnect, address 5
[ 1192.573238] pccard: card ejected from slot 0
[ 1195.515037] usb 1-2: new low speed USB device using uhci_hcd and address 6
[ 1195.689257] usb 1-2: configuration #1 chosen from 1 choice
[ 1195.708347] input: Dell Dell USB Mouse as /class/input/input6
[ 1195.708545] input: USB HID v1.10 Mouse [Dell Dell USB Mouse] on usb-0000:00:07.2-2
[ 6701.128682] pccard: PCMCIA card inserted into slot 0
[ 6701.129047] pcmcia: registering new device pcmcia0.0
[ 6706.304791] usb 1-2: USB disconnect, address 6
[ 6710.084792] hub 1-0:1.0: over-current change on port 2
[ 6710.428772] usb 1-2: new full speed USB device using uhci_hcd and address 7
[ 6710.599226] usb 1-2: configuration #1 chosen from 1 choice
[ 6819.201642] usb 1-2: USB disconnect, address 7
[ 6825.489632] usb 1-2: new low speed USB device using uhci_hcd and address 8
[ 6825.663263] usb 1-2: configuration #1 chosen from 1 choice
[ 6825.682337] input: Dell Dell USB Mouse as /class/input/input7
[ 6825.682532] input: USB HID v1.10 Mouse [Dell Dell USB Mouse] on usb-0000:00:07.2-2
[ 7000.894999] usb 1-1: USB disconnect, address 3
[ 7109.573907] pccard: card ejected from slot 0
[ 7111.775836] hub 1-0:1.0: over-current change on port 1
[ 7112.119800] usb 1-1: new full speed USB device using uhci_hcd and address 9
[ 7112.286151] usb 1-1: configuration #1 chosen from 1 choice
[ 7432.070258] usb 1-1: USB disconnect, address 9
[ 7436.354285] hub 1-0:1.0: over-current change on port 1
[ 7436.698257] usb 1-1: new full speed USB device using uhci_hcd and address 10
[ 7436.867857] usb 1-1: configuration #1 chosen from 1 choice
[ 7441.142330] usb 1-1: USB disconnect, address 10
[ 7443.914342] hub 1-0:1.0: over-current change on port 1
[ 7444.258312] usb 1-1: new full speed USB device using uhci_hcd and address 11
[ 7444.588143] usb 1-1: configuration #1 chosen from 1 choice
[ 7451.978407] usb 1-1: USB disconnect, address 11
[10179.143055] hub 1-0:1.0: over-current change on port 1
[10179.487030] usb 1-1: new full speed USB device using uhci_hcd and address 12
[10179.813464] usb 1-1: configuration #1 chosen from 1 choice
[10505.485840] usb 1-1: USB disconnect, address 12
[10911.208574] hub 1-0:1.0: over-current change on port 1
[10911.552548] usb 1-1: new full speed USB device using uhci_hcd and address 13
[10911.884831] usb 1-1: configuration #1 chosen from 1 choice
[11170.518543] usb 1-1: USB disconnect, address 13
[11211.846843] hub 1-0:1.0: over-current change on port 1
[11213.598835] usb 1-1: new full speed USB device using uhci_hcd and address 14
[11213.752414] usb 1-1: configuration #1 chosen from 1 choice
[11215.594667] usbcore: registered new interface driver libusual
[11216.396414] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[11216.396756] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[11216.671756] Initializing USB Mass Storage driver...
[11216.678292] scsi2 : SCSI emulation for USB Mass Storage devices
[11216.688350] usb-storage: device found at 14
[11216.688368] usb-storage: waiting for device to settle before scanning
[11216.688942] usbcore: registered new interface driver usb-storage
[11216.689235] USB Mass Storage support registered.
[11221.688432] usb-storage: device scan complete
[11221.693494] scsi 2:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4243N A102 PQ: 0 ANSI: 0
[11221.696105] scsi 2:0:0:0: Attached scsi generic sg1 type 5
[11221.877335] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[11221.877359] Uniform CD-ROM driver Revision: 3.20
[11221.878925] sr 2:0:0:0: Attached scsi CD-ROM sr0
[11715.542723] usb 1-1: USB disconnect, address 14
[12174.494127] hub 1-0:1.0: over-current change on port 1
[12176.246109] usb 1-1: new full speed USB device using uhci_hcd and address 15
[12176.399762] usb 1-1: configuration #1 chosen from 1 choice
[12176.403092] scsi3 : SCSI emulation for USB Mass Storage devices
[12176.403727] usb-storage: device found at 15
[12176.403741] usb-storage: waiting for device to settle before scanning
[12181.403449] usb-storage: device scan complete
[12181.406530] scsi 3:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4243N A102 PQ: 0 ANSI: 0
[12181.498390] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[12181.498605] sr 3:0:0:0: Attached scsi CD-ROM sr0
[12181.498765] sr 3:0:0:0: Attached scsi generic sg1 type 5
[12192.857932] ISO 9660 Extensions: Microsoft Joliet Level 3
[12192.894000] ISOFS: changing to secondary root
[12242.534643] usb 1-2: USB disconnect, address 8
[12250.598704] hub 1-0:1.0: over-current change on port 2
[12250.942693] usb 1-2: new full speed USB device using uhci_hcd and address 16
[12251.274549] usb 1-2: configuration #1 chosen from 1 choice
[12383.655975] usb 1-1: USB disconnect, address 15
[12386.427737] hub 1-0:1.0: over-current change on port 1
[12386.771807] usb 1-1: new full speed USB device using uhci_hcd and address 17
[12386.919156] usb 1-1: configuration #1 chosen from 1 choice
[12386.921041] hub 1-1:1.0: USB hub found
[12386.923888] hub 1-1:1.0: 4 ports detected
[12392.223802] hub 1-0:1.0: port 1 disabled by hub (EMI?), re-enabling...
[12392.223826] hub 1-0:1.0: over-current change on port 1
[12392.327748] usb 1-1: USB disconnect, address 17
[12392.439779] usb 1-1: new full speed USB device using uhci_hcd and address 18
[12392.587007] usb 1-1: configuration #1 chosen from 1 choice
[12392.588810] hub 1-1:1.0: USB hub found
[12392.591667] hub 1-1:1.0: 4 ports detected
[12393.981343] usb 1-1.4: new full speed USB device using uhci_hcd and address 19
[12394.112630] usb 1-1.4: configuration #1 chosen from 1 choice
[12394.115949] scsi4 : SCSI emulation for USB Mass Storage devices
[12394.116582] usb-storage: device found at 19
[12394.116596] usb-storage: waiting for device to settle before scanning
[12396.160876] usb 1-1.3: new low speed USB device using uhci_hcd and address 20
[12396.314144] usb 1-1.3: configuration #1 chosen from 1 choice
[12396.333278] input: Dell Dell USB Mouse as /class/input/input8
[12396.333474] input: USB HID v1.10 Mouse [Dell Dell USB Mouse] on usb-0000:00:07.2-1.3
[12399.117299] usb-storage: device scan complete
[12399.122345] scsi 4:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4243N A102 PQ: 0 ANSI: 0
[12399.155240] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[12399.155475] sr 4:0:0:0: Attached scsi CD-ROM sr0
[12399.155633] sr 4:0:0:0: Attached scsi generic sg1 type 5
[12813.822977] usb 1-2: USB disconnect, address 16
[12837.499119] usb 1-2: new full speed USB device using uhci_hcd and address 21
[12837.885483] usb 1-2: configuration #1 chosen from 1 choice
[13567.084628] pccard: PCMCIA card inserted into slot 0
[13567.084988] pcmcia: registering new device pcmcia0.0
adam@laptopB2131:~$ 

adam@laptopB2131:~$ dmesg | tail
[12399.122345] scsi 4:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4243N A102 PQ: 0 ANSI: 0
[12399.155240] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[12399.155475] sr 4:0:0:0: Attached scsi CD-ROM sr0
[12399.155633] sr 4:0:0:0: Attached scsi generic sg1 type 5
[12813.822977] usb 1-2: USB disconnect, address 16
[12837.499119] usb 1-2: new full speed USB device using uhci_hcd and address 21
[12837.885483] usb 1-2: configuration #1 chosen from 1 choice
[13567.084628] pccard: PCMCIA card inserted into slot 0
[13567.084988] pcmcia: registering new device pcmcia0.0
[15581.559993] usb 1-2: USB disconnect, address 21
adam@laptopB2131:~$ dmesg | tail
[12399.155240] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[12399.155475] sr 4:0:0:0: Attached scsi CD-ROM sr0
[12399.155633] sr 4:0:0:0: Attached scsi generic sg1 type 5
[12813.822977] usb 1-2: USB disconnect, address 16
[12837.499119] usb 1-2: new full speed USB device using uhci_hcd and address 21
[12837.885483] usb 1-2: configuration #1 chosen from 1 choice
[13567.084628] pccard: PCMCIA card inserted into slot 0
[13567.084988] pcmcia: registering new device pcmcia0.0
[15581.559993] usb 1-2: USB disconnect, address 21
[15726.004234] pccard: card ejected from slot 0
adam@laptopB2131:~$ 

adam@laptopB2131:~$ dmesg | tail
[12813.822977] usb 1-2: USB disconnect, address 16
[12837.499119] usb 1-2: new full speed USB device using uhci_hcd and address 21
[12837.885483] usb 1-2: configuration #1 chosen from 1 choice
[13567.084628] pccard: PCMCIA card inserted into slot 0
[13567.084988] pcmcia: registering new device pcmcia0.0
[15581.559993] usb 1-2: USB disconnect, address 21
[15726.004234] pccard: card ejected from slot 0
[16102.951851] hub 1-0:1.0: over-current change on port 2
[16103.295817] usb 1-2: new full speed USB device using uhci_hcd and address 22
[16103.626792] usb 1-2: configuration #1 chosen from 1 choice
adam@laptopB2131:~$ dmesg | tail
[12837.499119] usb 1-2: new full speed USB device using uhci_hcd and address 21
[12837.885483] usb 1-2: configuration #1 chosen from 1 choice
[13567.084628] pccard: PCMCIA card inserted into slot 0
[13567.084988] pcmcia: registering new device pcmcia0.0
[15581.559993] usb 1-2: USB disconnect, address 21
[15726.004234] pccard: card ejected from slot 0
[16102.951851] hub 1-0:1.0: over-current change on port 2
[16103.295817] usb 1-2: new full speed USB device using uhci_hcd and address 22
[16103.626792] usb 1-2: configuration #1 chosen from 1 choice
[16136.720112] usb 1-2: USB disconnect, address 22
adam@laptopB2131:~$ 

adam@laptopB2131:~$ dmesg | tail
[13567.084988] pcmcia: registering new device pcmcia0.0
[15581.559993] usb 1-2: USB disconnect, address 21
[15726.004234] pccard: card ejected from slot 0
[16102.951851] hub 1-0:1.0: over-current change on port 2
[16103.295817] usb 1-2: new full speed USB device using uhci_hcd and address 22
[16103.626792] usb 1-2: configuration #1 chosen from 1 choice
[16136.720112] usb 1-2: USB disconnect, address 22
[16375.869920] hub 1-0:1.0: over-current change on port 2
[16376.213895] usb 1-2: new full speed USB device using uhci_hcd and address 23
[16376.380660] usb 1-2: configuration #1 chosen from 1 choice
adam@laptopB2131:~$ dmesg | tail
[15581.559993] usb 1-2: USB disconnect, address 21
[15726.004234] pccard: card ejected from slot 0
[16102.951851] hub 1-0:1.0: over-current change on port 2
[16103.295817] usb 1-2: new full speed USB device using uhci_hcd and address 22
[16103.626792] usb 1-2: configuration #1 chosen from 1 choice
[16136.720112] usb 1-2: USB disconnect, address 22
[16375.869920] hub 1-0:1.0: over-current change on port 2
[16376.213895] usb 1-2: new full speed USB device using uhci_hcd and address 23
[16376.380660] usb 1-2: configuration #1 chosen from 1 choice
[16391.746047] usb 1-2: USB disconnect, address 23
adam@laptopB2131:~$ 

Sorry its so long.

---

### Post by Arthur Archnix on 2008-02-26
That's ok, just put code tags around them to fix it. What did you do there? That output doesn't look like you ran a (1) plugged in device (2) dmesg | tail (3) unplugged device (4) dmesg | tail.

In any event, it clearly shows that it's recognizing when things get plugged in. And it's recognizing at least one of the usb cards, and the pcmia card as well. First hurdle overcome.

Ok, so plug in the pcmcia card, and type:
```
sudo lshw
```
Make sure to wrap the output in code tags this time. They look like #

---

### Post by Adam.W on 2008-02-26
This is what I got:

adam@laptopB2131:~$ sudo lshw
[sudo] password for adam:
laptopb2131               
    description: Notebook
    product: LIFEBOOK B Series
    vendor: FUJITSU SIEMENS
    serial: YBRG007965
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: administrator_password=disabled boot=normal chassis=notebook keyboard_password=disabled power-on_password=disabled uuid=168AC121-2F2D-11D4-8B14-00000ED2F8D0
  *-core
       description: Motherboard
       product: CHIFFON
       vendor: FUJITSU
       physical id: 0
       slot: Mouse
     *-firmware
          description: BIOS
          vendor: Phoenix/FUJITSU
          physical id: 0
          version: Version  1.07 (11/30/1999)
          size: 80KB
          capacity: 448KB
          capabilities: pci pcmcia pnp apm upgrade shadowing bootselect edd int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi biosbootspecification netboot
     *-cpu
          description: CPU
          product: Celeron (Coppermine)
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.8.1
          slot: Onboard
          size: 400MHz
          capacity: 400MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 32KB
             capacity: 32KB
             capabilities: internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 128KB
             capacity: 128KB
             capabilities: pipeline-burst synchronous internal write-back unified
     *-memory
          description: System Memory
          physical id: 1d
          slot: System board or motherboard
          size: 128MB
          capacity: 192MB
        *-bank:0
             description: Row of chips SDRAM Synchronous 100 MHz (10.0 ns)
             physical id: 0
             slot: Onboard
             size: 64MB
             width: 64 bits
             clock: 100MHz (10.0ns)
        *-bank:1
             description: DIMM SDRAM Synchronous 100 MHz (10.0 ns)
             physical id: 1
             slot: DIMM1
             size: 64MB
             width: 64 bits
             clock: 100MHz (10.0ns)
     *-pci
          description: Host bridge
          product: 82440MX Host Bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 33MHz
          configuration: latency=64
        *-multimedia
             description: Multimedia audio controller
             product: 82440MX AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0
        *-bridge:0 UNCLAIMED
             description: Bridge
             product: 82440MX ISA Bridge
             vendor: Intel Corporation
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bridge bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82440MX EIDE Controller
             vendor: Intel Corporation
             physical id: 7.1
             bus info: pci@0000:00:07.1
             logical name: scsi0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=64 module=ata_piix
           *-disk
                description: SCSI Disk
                product: FUJITSU MHH2064A
                vendor: ATA
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: BC16
                serial: 01081350
                size: 5729MB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: Linux filesystem partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 5428MB
                   capabilities: primary bootable
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 298MB
                   capacity: 298MB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 298MB
                      capabilities: nofs
        *-usb
             description: USB Controller
             product: 82440MX USB Universal Host Controller
             vendor: Intel Corporation
             physical id: 7.2
             bus info: pci@0000:00:07.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=64 module=uhci_hcd
        *-bridge:1
             description: Bridge
             product: 82440MX Power Management Controller
             vendor: Intel Corporation
             physical id: 7.3
             bus info: pci@0000:00:07.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bridge
             configuration: driver=piix4_smbus latency=0 module=i2c_piix4
        *-network
             description: Ethernet interface
             product: 82557/8/9 Ethernet Pro 100
             vendor: Intel Corporation
             physical id: 10
             bus info: pci@0000:00:10.0
             logical name: eth0
             version: 08
             serial: 00:00:0e:d2:f8:d0
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI duplex=full firmware=N/A ip=192.168.254.50 latency=66 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
        *-communication UNCLAIMED
             description: Communication controller
             product: F-1156IV WinModem (V90, 56KFlex)
             vendor: Agere Systems
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0 maxlatency=14 mingnt=252
        *-pcmcia
             description: CardBus bridge
             product: PCI1410 PC card Cardbus Controller
             vendor: Texas Instruments
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
           *-network
                description: PRISM ISL37101P-SSF Adapter
                product: ISL37101P-10
                vendor: Intersil
                physical id: 0
                version: A3
                slot: Socket 0
        *-display
             description: VGA compatible controller
             product: Cyber 9525
             vendor: Trident Microsystems
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 49
             width: 32 bits
             clock: 66MHz
             capabilities: agp agp-1.0 pm vga bus_master cap_list
             configuration: latency=64
     *-scsi
          physical id: 1
          bus info: usb@1:1.4
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-cdrom
             description: DVD reader
             product: RW/DVD GCC-4243N
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/dvd
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: A102
             capabilities: removable audio cd-r cd-rw dvd
             configuration: status=open
  *-battery
       description: Lithium Ion Battery
       product: CP024601-XX
       vendor: FUJITSU
       physical id: 1
       serial: 01
       slot: Internal Battery
       capacity: 28080mWh
       configuration: voltage=10.8V
adam@laptopB2131:~$ 

What do mean by code tags?

---

### Post by james_vanb on 2008-02-26
You may be way past this, but I'm using the Belkin Wireless g usb to post this reply.  I think you posted previously that you downloaded the install files from the Belkin web site.  If you have the install cd that came with the adapter, use it.  The web site has a number of install files.  Not all of them will work.  You may have to download different versions to make it work.  If you have the original cd - use it.  I used ndiswrapper to get mine working. The process is as follows:

Unplug adapter before you boot.

Install ndiswrapper through Synaptic.

Open terminal.

Remove the following drivers using these commands (If not using Xubuntu, substitute commands as appropriate):

sudo modprobe -r rt2500usb
sudo modprobe -r rt73usb

'm not sure that this actually removes the drivers, but after 3 weeks of farting around with them it made me feel better.

Blacklist rt2500usb and rt73usb by opening text editor (My default is mousepad) as follows:

sudo mousepad /etc/modprobe.d/blacklist

add rt2500usb and rt73usb to end of list, save and close.

**REBOOT**

This is where the guides I was following failed. Blacklist doesn't work until you reboot. If you don't, the wrong driver will be associated.

On your desktop, open "Home" - right click in an open area and create a file - I called mine "Belkin".
Insert the install cd. Open and navigate to the driver file under XP. there will be 3 files. Copy all 3 files to the file you created under "Home" by dragging and dropping.  **The drivers will not load directly from the cd.**

Now install the driver you just copied with the following :

sudo ndiswrapper -i /home/(your user name)/Belkin/rt73.inf

Insert the wireless adapter.

Now issue the following commands:

sudo depmod -a
sudo modprobe ndiswrapper

I think these create the module. Now edit modules to load ndiswrapper when you boot as follows:

sudo mousepad /etc/modules

Add "ndiswrapper" (without quotes) to the end of the list.

Establish alias with following command:

sudo ndiswrapper -m

Reboot

You should now have a connection. Roaming mode works sporadically, so I manually configure. Left click on the network manager at the upper right corner and enter manual configuration. Open wifi properties. Untick "enable roaming". Next to Network name, you should be able to click on the arrow and a drop down will show available networks, click on yours. Set Password type to WPA personal. Set Configuration to Automatic configuration (DHCP). I don't use WEP yet, but if you do, you may have to enter your password in Network password.

---

### Post by anewguy on 2008-02-26
james_vanb  - you posted what I also did to get my Belkin USB G wireless working.  Nice response.  I sometimes wish people would just recommend using ndiswrapper right off the bat instead of going through a "zillion" hoops first only to find you need to use ndiswrapper anyway.  Good post!

---

### Post by james_vanb on 2008-02-26
anewguy - Thanks for your kind reply.  As a Noob that tried the "zillion hoops" - Followed by no less than 5 clean reinstalls to fix the damage - I'm glad to hear this worked for someone else.  There's something to be said for simplicity.  Thanks again for your encouraging reply.

---

### Post by Adam.W on 2008-02-27
I don't have the Belkin CD and the drivers I downloaded and put on CD don't seen to work?

Any idears?

I Have a Netgear WG111v3 and I think I have the CD for that. What do I have to change in your setup to make that one work?

Thanks

---

### Post by james_vanb on 2008-02-27
The Belkin site has a number of different instal versions.  I once misplaced my original cd - Downloaded the most recent version listed for xp - It didn't work.  Then downloaded the one for ME and it worked.  Go figure.  If you can, download and burn to a cd.  When you open the cd, look for the drivers listed for xp.  There should be 3 - rt73.cat, rt73.inf and rt73.sys.

They won't load directly from the cd.  You have to copy them to your desktop and then load.

If your downloading directly to your desktop, you'll get a .exe file.  There might be a way to open and load, but I don't how.  Burn to a cd.

Let us know how it goes.

---

### Post by james_vanb on 2008-02-27
I just tried to upload the drivers I'm using to this post - Didn't work.  Do you want me to try sending via e-mail?

---

### Post by Adam.W on 2008-02-27
If you dont mind. My email address is 

[email]adam.woodard@djblaw.co.uk[/email]

Thanks

---

### Post by Adam.W on 2008-02-29
In the end I reinstalled Xubuntu and now it works. I just pluged it in and it worked? I didnt install anything or change anything I just pluged it in. 

I have problems connecting sometimes but only to networks with passwords? 

If anybody has had this problem in the past and solved it please let me know.

Thanks for all your help.

now on to my next two tasks Bluetooth and the touchscreen? (feel free to give advice ;) )

Adam

---

### Post by james_vanb on 2008-02-29
Go figure!!

Glad to hear you're up and running.

---

