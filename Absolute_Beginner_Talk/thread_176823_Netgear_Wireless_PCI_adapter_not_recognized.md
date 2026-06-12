---
title: "Netgear Wireless PCI adapter not recognized"
date: 2006-05-15
forum: Absolute Beginner Talk
---

### Post by ahlandberg on 2006-05-15
Ubuntu recognizes my wired ethernet adapter (eth0) but not my wireless PCI adapter (which used to work under winXP).

When I use iwconfig it tells me that there are no wireless extensions.

What could be a reason for it not recognizing my wlan card?

Thanks in advance!

Cheers, Anders

---

### Post by skippy81 on 2006-05-15
Some info which will help us to help you:

1) Name/model number of your card.  Needs to be exact - ie Netgear MA101 rev2. 

2) Open a terminal and type "lspci" into it.  Copy the text and paste it to the forums.  

3) In the same terminal run "dmesg".  See if there is anything relevant to networking devices in it.  If there is paste it :D


If your lucky, your card is supported with a built in kernel module which we can just activate.  If not then there is a cool utility called "ndiswrapper" which will sometimes allow you to use windows drivers to operate a network card in linux.

---

### Post by ahlandberg on 2006-05-15
Hi! Thanks foir the tips!

Here what I found out:

1) Name/model number of your card. Needs to be exact - ie Netgear MA101 rev2.

NETGEAR WG311 v3 54Mbps

2) Open a terminal and type "lspci" into it. Copy the text and paste it to the forums.

ahlandberg@ubuntu:~/java$ lspci
0000:00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (r ev a2)
0000:00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev a2)
0000:00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev a2)
0000:00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev a2)
0000:00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev a2)
0000:00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev a2)
0000:00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a3)
0000:00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3)
0000:00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3)
0000:00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3)
0000:00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller  (rev a1)
0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
0000:00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
0000:00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
0000:00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev a2)
0000:01:08.0 Ethernet controller: Marvell Technology Group Ltd.: Unknown device 1faa (rev 03)
0000:02:00.0 VGA compatible controller: nVidia Corporation NV28 [GeForce4 Ti 420 0 AGP 8x] (rev a1)


3) In the same terminal run "dmesg". See if there is anything relevant to networking devices in it. If there is paste it 

ahlandberg@ubuntu:~/java$ dmesg
ort0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[4294688.456000] lp0: using parport0 (interrupt-driven).
[4294688.478000] mice: PS/2 mouse device common for all mice
[4294688.760000] logips2pp: Detected unknown logitech mouse model 1
[4294688.847000] input: PS/2 Logitech Mouse on isa0060/serio1
[4294689.049000] ts: Compaq touchscreen protocol output
[4294691.873000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294693.257000] Linux agpgart interface v0.101 (c) Dave Jones
[4294693.264000] agpgart: Detected NVIDIA nForce2 chipset
[4294693.309000] agpgart: AGP aperture is 512M @ 0xa0000000
[4294693.625000] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x5000
[4294693.638000] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x5500
[4294693.974000] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 21
[4294693.974000] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [APCJ] -> GSI 21 (level, high) -> IRQ 21
[4294693.974000] PCI: Setting latency timer of device 0000:00:06.0 to 64
[4294694.286000] intel8x0_measure_ac97_clock: measured 49782 usecs
[4294694.286000] intel8x0: clocking to 47474
[4294694.870000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294694.883000] shpchp: shpc_init : shpc_cap_offset == 0
[4294694.883000] shpchp: shpc_init : shpc_cap_offset == 0
[4294694.883000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294696.244000] Real Time Clock Driver v1.12
[4294696.286000] input: PC Speaker
[4294696.423000] Floppy drive(s): fd0 is 1.44M
[4294696.438000] FDC 0 is a post-1991 82077
[4294697.480000] eth0: no link during initialization.
[4294739.508000] ACPI: Power Button (FF) [PWRF]
[4294739.508000] ACPI: Power Button (CM) [PWRB]
[4294739.602000] ibm_acpi: ec object not found
[4294930.018000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[4294930.018000] apm: overridden by ACPI.
[4294930.035000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[4294930.035000] apm: disabled on user request.
[4294945.941000] Bluetooth: Core ver 2.7
[4294945.941000] NET: Registered protocol family 31
[4294945.941000] Bluetooth: HCI device and connection manager initialized
[4294945.941000] Bluetooth: HCI socket layer initialized
[4294945.954000] Bluetooth: L2CAP ver 2.7
[4294945.954000] Bluetooth: L2CAP socket layer initialized
[4294945.975000] Bluetooth: RFCOMM ver 1.5
[4294945.975000] Bluetooth: RFCOMM socket layer initialized
[4294945.975000] Bluetooth: RFCOMM TTY layer initialized
[4295044.106000] ibm_acpi: ec object not found
[4295099.711000] NET: Registered protocol family 10
[4295099.712000] Disabled Privacy Extensions on device c02eb280(lo)
[4295099.712000] IPv6 over IPv4 tunneling driver
[4295110.079000] eth0: no IPv6 routers present
[4295223.408000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[4295223.408000] apm: disabled on user request.
[4295237.969000] ppdev: user-space parallel port driver
[4295237.969000] ppdev0: registered pardevice
[4295238.012000] ppdev0: unregistered pardevice
[4295238.012000] ppdev1: claim the port first
[4295238.012000] ppdev2: claim the port first
[4295324.517000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[4295324.517000] apm: disabled on user request.
[4295492.319000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295492.319000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295492.434000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295492.434000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295506.474000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295506.474000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295506.589000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295506.589000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295512.177000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295512.177000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295512.309000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295512.309000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295512.814000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295512.814000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295513.032000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295513.032000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295514.655000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295514.655000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295514.779000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295514.779000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295521.777000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295521.777000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295521.883000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295521.883000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296152.501000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296152.501000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296152.608000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296152.608000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296152.758000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296152.758000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296152.869000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296152.869000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296152.975000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296152.975000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296153.090000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296153.090000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296153.162000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296153.162000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296153.265000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296153.265000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296153.329000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296153.329000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296153.440000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296153.440000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296153.680000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296153.680000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296153.804000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296153.804000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4298395.225000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[4298395.225000] apm: disabled on user request.
[4298882.485000] eth0: no link during initialization.
[4298882.509000] NET: Registered protocol family 17
[4298892.710000] eth0: no IPv6 routers present
[4299000.634000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4299000.634000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299000.753000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4299000.753000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299001.165000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4299001.165000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299001.263000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4299001.263000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299001.364000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4299001.364000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299001.449000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4299001.449000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299001.538000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4299001.538000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299001.619000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4299001.619000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299001.692000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4299001.692000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299001.781000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4299001.781000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299290.695000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4299290.695000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299290.811000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4299290.811000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299413.622000] eth0: no link during initialization.
[4299418.471000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4299418.471000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299418.604000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4299418.604000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4299423.629000] eth0: no IPv6 routers present
[4300475.984000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4300475.984000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4300476.095000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4300476.095000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4300476.282000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4300476.282000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4300476.371000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4300476.371000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4300476.452000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4300476.452000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4300476.529000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4300476.529000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4300476.622000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4300476.622000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4300476.698000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4300476.698000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4300476.779000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4300476.779000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4300476.860000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4300476.860000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4300476.933000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4300476.933000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4300477.005000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4300477.005000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4300477.069000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4300477.069000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4300477.150000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4300477.150000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4300514.795000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4300514.795000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4300514.863000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4300514.863000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4300515.115000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4300515.115000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4300515.847000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4300515.847000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4300515.985000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4300515.985000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4300516.079000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4300516.079000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4300516.152000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4300516.152000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4300516.232000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4300516.232000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4300516.321000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4300516.321000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4300516.368000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4300516.368000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4309821.102000] ohci_hcd 0000:00:02.0: wakeup
[4309821.533000] usb 1-3: new full speed USB device using ohci_hcd and address 2
[4309821.882000] Initializing USB Mass Storage driver...
[4309821.888000] scsi0 : SCSI emulation for USB Mass Storage devices
[4309821.890000] usb-storage: device found at 2
[4309821.890000] usb-storage: waiting for device to settle before scanning
[4309821.890000] usbcore: registered new driver usb-storage
[4309821.890000] USB Mass Storage support registered.
[4309826.895000]   Vendor:           Model:                   Rev:
[4309826.895000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[4309826.902000] usb-storage: device scan complete
[4309826.992000] SCSI device sda: 254781 512-byte hdwr sectors (130 MB)
[4309827.005000] sda: Write Protect is off
[4309827.005000] sda: Mode Sense: 0b 00 00 08
[4309827.005000] sda: assuming drive cache: write through
[4309827.036000] SCSI device sda: 254781 512-byte hdwr sectors (130 MB)
[4309827.049000] sda: Write Protect is off
[4309827.049000] sda: Mode Sense: 0b 00 00 08
[4309827.049000] sda: assuming drive cache: write through
[4309827.049000]  /dev/scsi/host0/bus0/target0/lun0: p1
[4309827.157000] Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0
[4309827.734000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4309862.106000] usb 1-3: USB disconnect, address 2




Sorry for flooding this thread, but that what it displayed.

I don't know what most of it means but I noticed these things:

[4294697.480000] eth0: no link during initialization.
[4295110.079000] eth0: no IPv6 routers present

Don't know whether this has anything to do with my problem!?

Thanks in advance!

Cheers, Anders

---

### Post by skippy81 on 2006-05-15
OK lets get started.  

Open a terminal please and type "uname -r". This will give you the full name of the version of the linux kernel you are using.  

Next I want you to open the synaptic package manager (System > Admin > Synaptic), this assumes your using gnome.

Search synaptic for "Madwifi".  You will get a few packages called 'linux-restricted-modules........' come up.  You need to select and install the package which matches your kernel name as given to you by the uname -r command.

Get doing that while I write the next load of instructions :D

---

### Post by ahlandberg on 2006-05-15
Hi!

Thanks for youe help!

>Open a terminal please and type "uname -r". This will give you the full name of the version of the linux kernel you are using.

2.6.12-9-386

>Next I want you to open the synaptic package manager (System > Admin > Synaptic), this assumes your using gnome.

>Search synaptic for "Madwifi". You will get a few packages called 'linux-restricted-modules........' come up. You need to select and install the package which matches your kernel name as given to you by the uname -r command.

>Get doing that while I write the next load of instructions

Ok, I searched for madwifi and it found one entry:

linux-restricted-modules-2.6.12-9-386 2.6.12.4-11 2.6.12.4-11 Non-free Linux 2.6.12 modules on 386

It appears that this module already is installed, so I re-installed it now.

---

### Post by skippy81 on 2006-05-15
OK good, now you can activate the interface :) 

Start off by typing > sudo modprobe ath_pci in a terminal.   This will load the main driver for your card.

Now when you type ifconfig you should see your card appear as ath0
> sudo ifconfig

If it doesnt appear as ath0 then, and only then, type:

> sudo wlanconfig ath0 create wlandev wifi0 wlanmode sta

OK, your card should definately be listed under "ifconfig" as ath0 now.  If it isnt then post back, otherwise move onwards to victory :)

From here on you will need to configure your card to work with your access point.  Here is a guide.  I have taken you through the ubuntu specific part. Follow [this guide]("http://http://madwifi.org/wiki/UserDocs/FirstTimeHowTo") from "Scanning for Access Points" onwards and you should be ok.  

Edit When following the guide I linked to, put the word "sudo" before every command they list.

Good luck

---

### Post by ahlandberg on 2006-05-15
Hey again!

After executing sudo modprobe ath_pci and then ifconfig, the ath0 was still not there.

So I executed wlanconfig ..., and it gave me this error: command not found

I don't understand!?

Sorry for this but something seems to be really wrong.

Thanks for your help!

Cheers, Anders

---

### Post by skippy81 on 2006-05-15
Ok type this in:

> lsmod | grep ath

and paste its output.  If it doesnt give any output then the module isnt loaded right.

---

### Post by ahlandberg on 2006-05-15
Here is the output:

ahlandberg@ubuntu:~$ lsmod | grep ath
ath_pci                69148  0
ath_rate_sample        14344  1 ath_pci
wlan                  120988  2 ath_pci,ath_rate_sample
ath_hal               148432  2 ath_pci,ath_rate_sample

---

### Post by ahlandberg on 2006-05-15
Here the output:


ahlandberg@ubuntu:~$ lsmod | grep ath
ath_pci                69148  0
ath_rate_sample        14344  1 ath_pci
wlan                  120988  2 ath_pci,ath_rate_sample
ath_hal               148432  2 ath_pci,ath_rate_sample

---

### Post by skippy81 on 2006-05-15
wierd, it should work.   Have a quick try and use "system > administration > network" on the menu bar and see if it shows up there.  If not reboot your PC and see if that helps doing "ifconfig".

---

### Post by ahlandberg on 2006-05-15
Am rebooting now.

I installed ndiswrapper - maybe I can use the win drivers? But that again is nonsense because when I checked for existing drivers it showed the one for my kernel version.

I disabled the eth0. Now it shows the loopback connection (lo) under network connections.

I don't get it. Will try the codes you gave me again.

Thanks a lot for your help and patiance, will probably be back tomorrow.
It's late, I need to sleep.

Cheers, Anders

---

### Post by skippy81 on 2006-05-15
OK mate, sorry I made a mistake.  I wrongly assumed your card would work with the atheros driver, but this is not the case :(  As a revision 3 card your wifi uses a wierd chipset by  Marvell.

You can still *probably* get it working though.  

You need the cd that came with the network card. It will have windows drivers on it.

You need to find 2 drivers called WG311v3.INF and WG311v3XP.sys and copy them into your linux home directory (get at it with the places menu bar).

Once you have copied them into your places you need to install "ndiswrapper-utils" package using synaptic.  

Next you need to type the following in a terminal
 > sudo cp *.inf *.sys /etc/ndiswrapper/

followed by > sudo ndiswrapper -i WG311v3.INF 

finally type > sudo ndiswrapper -l 

It should say something like "hardware present", if it does then continue :-

> sudo depmod -a

and finally 

> sudo modprobe ndiswrapper

do an ifconfig or use the network graphical tool and see if the card is detected.

---

### Post by skippy81 on 2006-05-15
oh and to take down the atheros drivers which didnt work you can do

> sudo rmmod ath_rate_sample
sudo rmmod ath_hal
sudo rmmod ath_pci

---

### Post by ahlandberg on 2006-05-15
Thanks for finding out about that!! Great!

Just one last little problem: it doesn't let me do the ndiswrapper -i WG311v3.INF :

'Unable to create directory. Make sure you're running as root.'

How can I login as root????

---

### Post by tkjacobsen on 2006-05-15
use "sudo -i"  to change to root user. Or just use  sudo before your command:
```
sudo ndiswrapper -i WG311v3.INF
```
then you will execute the command as root user

---

### Post by ahlandberg on 2006-05-15
You're a gun! The connection is there. Should I have it on DHCP or static IP?

---

### Post by ahlandberg on 2006-05-15
In 'Network Settings' it now says:

Wireless Connection
The interface wlan0 is active

Key Type: Plain
Configuration: DHCP

Everythings seems to look fine but when opening Firefox I cannot open internet pages. Does is maybe take a while until the changes take effect?

By the way, when logging off, do I need to tick (save current setup) in order to keep the changes?

---

### Post by tkjacobsen on 2006-05-16
Chece if your interface eth0 is active. maybe eth0 is set to be the default gateway (can be set in networking), instead wlan0 should be the default gateway.

I don't think it is necessary to save the settings to keep them after boot.

I would use DHCP - unless you really know how to set up your router.

---

### Post by deadlycow21 on 2006-06-27
don't know how to delete a post....

---

