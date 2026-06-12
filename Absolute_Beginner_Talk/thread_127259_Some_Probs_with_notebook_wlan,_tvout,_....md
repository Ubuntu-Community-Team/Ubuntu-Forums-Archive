---
title: "Some Probs with notebook: wlan, tvout, ..."
date: 2006-02-08
forum: Absolute Beginner Talk
---

### Post by Traudel on 2006-02-08
Hi, i'm new to Ubuntu. I installed the os several times on my hp nx6125 notebook. after getting things managed with noapic nolapic etc there still remain problems to me:

1) i've followed several guides found on this forum, all haven't worked out for me, so here's problem one: i have a Broadcom 802.11b/g BCM 4xxx wlan device, which i got working running opensuse/suse10 by using windows *.inf/*.sys with ndiswrapper. Meaning:
- ndiswrapper -i bcmwl5a.inf
- ndiswrapper -m
- ndiswrapper -hotplug
- Creating a custom wlancard in controlpanel with modulname ndiswrapper; making wireless secure settings; after reboot blue wireless led showed up on notebook; connected to wlan; worked fine

i've tryed same using ubuntu, doing ndiswrapper -hotplug doen's start blue wireless led as in suse, but wlan0 never the less was added unter networksetting.
i set up wlan security, meaning network name, key, dhcp, but wlan0 remains idle, transfers no pakets at all.
i'm using ACL, WEP-PSK and WPA.

2) after fixed problem with black and white picture in tv-out (clone) mode i still got problems with overlay, meaning: i have fine picture of desktop etc, but when starting kaffeine and play a video, no video is shown on tv. already tryed serveral attemps zu fix this issue, without success.

3) my notebook features a texas instruments multi format card reader, which isn't recognized during the setup. also tryed some tutorial here, also no success.

hope someone can help me with one or more of my problems.

::sorry for my bad english... :(

---

### Post by TrendyDark on 2006-02-08
Can you show the output of the terminal command "ifconfig wlan0"?

---

### Post by Traudel on 2006-02-08
[QUOTE=TrendyDark]Can you show the output of the terminal command "ifconfig wlan0"?[/QUOTE]

```
wlan0     Protokoll:Ethernet  Hardware Adresse 00:14:A5:19:8C:3D
          BROADCAST MULTICAST  MTU:1500  Metric:1
          Speicher:c4010000-c4011fff
```

---

### Post by TrendyDark on 2006-02-08
I believe that means it's not configured correctly. Try making sure that you're settings are correct and then type this in terminal:

```
sudo ifup wlan0
```

---

### Post by Traudel on 2006-02-08
did everything like i did on my suse system, also tryed "special" ubuntu guides.
did:
- ndiswrapper -i infname.inf
- ndiswrapper -m
- ndiswrapper -hotplug
- modprobe ndiswrapper
- configured wlan card via network settings, set ESSID, WEP-Key and DHCP Setting, then activated card. trying to set standart gateway to wlan0 doesnt work, stats say device is idle.

"sudo ifup wlan0" output:
```
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Invalid argument.
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:14:a5:19:8c:3d
Sending on   LPF/wlan0/00:14:a5:19:8c:3d
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

---

### Post by TrendyDark on 2006-02-08
Hmm. . .I'm stumped. The driver seems to be working correctly, but it's not connecting to your network. Maybe see if it's something to do with your network setup, your router settings and such.

---

### Post by Traudel on 2006-02-08
hat no problems connecting via windows or suse, also tryed switching of network security and still got no connect :(

---

### Post by TrendyDark on 2006-02-08
okay, try "ndiswrapper -i" once you've installed the driver, see if it's detecting the hardware at least.

it should look something like this (i use ndiswrapper):

```
jeremiah@ubuntu:~$ ndiswrapper -l
Installed ndis drivers:
mrv8000c        driver present, hardware present

```

---

### Post by Traudel on 2006-02-08
as mentioned ndiswrapper -l works fine:
bcmwl5a        driver present, hardware present...

---

### Post by TrendyDark on 2006-02-08
I'm all out of ideas. Sorry lol If it's not getting a DHCP request from your network, and the hardware works, then it has to either be your network or configuration. Both of which seem to be fine.

---

### Post by Traudel on 2006-02-09
maybe someone els got a clue :(

---

### Post by Traudel on 2006-02-09
isn't there anyone managed to get the wlan adapter working, cause in this forum are so many threads about that issue :(

---

### Post by pelle.k on 2006-02-09
Yeah, some obvious, but easily forgotten things;
have you set the right channel, also essid >>IS<< case sensitive.

Can i see the output of iwconfig wlan0?

Also how did you install ndiswrapper (i suppose synaptic?)

Give us output of dmesg.

About the tv-out. What resolution are you using on your monitor? (not tv)

---

### Post by Traudel on 2006-02-09
essid is lowercase as configured on the router.

[QUOTE=iwconfig wlan0]
wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[/QUOTE]

i installed ndiswrapper via "apt-get install ndiswraper-utils"


[QUOTE=dmesg]294710.299000]   options:  [pci] [cardbus] [pm]
[4294710.311000] ACPI: PCI Interrupt Link [C0F3] enabled at IRQ 11
[4294710.311000] ACPI: PCI Interrupt 0000:02:04.0[A] -> Link [C0F3] -> GSI 11 (level, low) -> IRQ 11
[4294710.311000] Yenta: CardBus bridge found at 0000:02:04.0 [103c:308b]
[4294710.311000] Yenta: Enabling burst memory read transactions
[4294710.311000] Yenta: Using INTVAL to route CSC interrupts to PCI
[4294710.311000] Yenta: Routing CardBus interrupts to PCI
[4294710.311000] Yenta TI: socket 0000:02:04.0, mfunc 0x01a11b22, devctl 0x64
[4294710.532000] Yenta: ISA IRQ mask 0x0078, PCI irq 11
[4294710.532000] Socket status: 30000006
[4294710.608000] ohci1394: $Rev: 1250 $ Ben Collins <bcollins@debian.org>
[4294710.608000] ACPI: PCI Interrupt Link [C0F4] enabled at IRQ 9
[4294710.608000] PCI: setting IRQ 9 as level-triggered
[4294710.608000] ACPI: PCI Interrupt 0000:02:04.2[C] -> Link [C0F4] -> GSI 9 (level, low) -> IRQ 9
[4294710.662000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[9]  MMIO=[c4013000-c40137ff]  Max Packet=[2048]
[4294711.922000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023f992991390a][4294712.448000] input: PC Speaker
[4294712.482000] Real Time Clock Driver v1.12
[4294714.214000] NET: Registered protocol family 17
[4294715.794000] tg3: eth0: Link is up at 100 Mbps, full duplex.
[4294715.794000] tg3: eth0: Flow control is on for TX and on for RX.
[4294727.484000] NET: Registered protocol family 10
[4294727.484000] Disabled Privacy Extensions on device c0321b80(lo)
[4294727.484000] IPv6 over IPv4 tunneling driver
[4294728.787000] ACPI: AC Adapter [C173] (on-line)
[4294728.849000] ACPI: Power Button (FF) [PWRF]
[4294728.849000] ACPI: Sleep Button (CM) [C1EC]
[4294728.849000] ACPI: Lid Switch [C1ED]
[4294728.899000] ibm_acpi: ec object not found
[4294728.943000] ACPI: Battery Slot [C175] (battery present)
[4294728.943000] ACPI: Battery Slot [C174] (battery absent)
[4294728.956000] ACPI: Video Device [C048] (multi-head: yes  rom: no  post: no)
[4294728.968000] wmi_add device=dde1c800
[4294728.968000] calling WQBA
[4294736.064000] [fglrx] Maximum main memory to use for locked dma buffers: 403 MBytes.
[4294736.064000] ACPI: PCI Interrupt 0000:01:05.0[A] -> Link [C0F0] -> GSI 11 (level, low) -> IRQ 11
[4294736.064000] [fglrx] module loaded - fglrx 8.16.20 [Aug 16 2005] on minor 0
[4294736.088000] [fglrx] free  PCIe = 54804480
[4294736.088000] [fglrx] max   PCIe = 54804480
[4294736.088000] [fglrx] free  LFB = 21950464
[4294736.088000] [fglrx] max   LFB = 21950464
[4294736.088000] [fglrx] free  Inv = 0
[4294736.088000] [fglrx] max   Inv = 0
[4294736.088000] [fglrx] total Inv = 0
[4294736.088000] [fglrx] total TIM = 0
[4294736.088000] [fglrx] total FB  = 0
[4294736.088000] [fglrx] total PCIe = 16384
[4294737.340000] apm: BIOS not found.
[4294737.803000] eth0: no IPv6 routers present
[4294738.429000] cs: IO port probe 0x100-0x4ff: clean.
[4294738.433000] cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xc10-0xc17 0xc50-0xc57 0xc68-0xc6f 0xcd0-0xcdf
[4294738.434000] cs: IO port probe 0xa00-0xaff: clean.
[4294738.834000] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.40.4)
[4294738.836000] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x8 (1350 mV)
[4294738.836000] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0xa (1300 mV)
[4294738.836000] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x13 (1075 mV)
[4294738.837000] cpu_init done, current fid 0xa, vid 0x6
[4294738.856000] powernow-k8: ph2 null fid transition 0xa
[4294739.525000] drivers/usb/input/hid-core.c: input irq status -71 received
[4294739.668000] Bluetooth: Core ver 2.7
[4294739.668000] NET: Registered protocol family 31
[4294739.668000] Bluetooth: HCI device and connection manager initialized
[4294739.669000] Bluetooth: HCI socket layer initialized
[4294739.746000] Bluetooth: L2CAP ver 2.7
[4294739.746000] Bluetooth: L2CAP socket layer initialized
[4294739.777000] Bluetooth: RFCOMM ver 1.5
[4294739.777000] Bluetooth: RFCOMM socket layer initialized
[4294739.777000] Bluetooth: RFCOMM TTY layer initialized
[4294746.478000] drivers/usb/input/hid-core.c: input irq status -71 received
[4294747.622000] drivers/usb/input/hid-core.c: input irq status -71 received
[4294749.350000] drivers/usb/input/hid-core.c: input irq status -71 received
[4294756.736000] drivers/usb/input/hid-core.c: input irq status -71 received
[4294759.952000] drivers/usb/input/hid-core.c: input irq status -71 received
[4294761.824000] drivers/usb/input/hid-core.c: input irq status -71 received
[4294764.353000] drivers/usb/input/hid-core.c: input irq status -71 received
[4294769.329000] drivers/usb/input/hid-core.c: input irq status -71 received
[4294787.268000] drivers/usb/input/hid-core.c: input irq status -71 received
[4294807.903000] drivers/usb/input/hid-core.c: input irq status -71 received
[4294844.813000] drivers/usb/input/hid-core.c: input irq status -71 received
[4294848.630000] drivers/usb/input/hid-core.c: input irq status -71 received
[4294854.798000] drivers/usb/input/hid-core.c: input irq status -71 received
[4294861.608000] drivers/usb/input/hid-core.c: input irq status -71 received
[4294866.224000] drivers/usb/input/hid-core.c: input irq status -71 received
[4294876.322000] drivers/usb/input/hid-core.c: input irq status -71 received
[4294899.981000] drivers/usb/input/hid-core.c: input irq status -71 received
[4294900.279000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4294900.279000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4294901.767000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4294901.767000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4294903.630000] drivers/usb/input/hid-core.c: input irq status -71 received
[4294910.179000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4294910.179000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4294911.687000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4294911.687000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4294912.111000] drivers/usb/input/hid-core.c: input irq status -71 received
[4294914.050000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4294914.050000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4294915.467000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4294915.467000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4294915.936000] drivers/usb/input/hid-core.c: input irq status -71 received
[4294916.825000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4294916.825000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4294918.313000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4294918.313000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4294924.446000] usb 2-3: USB disconnect, address 3
[4294926.373000] usb 2-3: new low speed USB device using ohci_hcd and address 4
[4294926.506000] input: USB HID v1.10 Mouse [Logitech USB Mouse] on usb-0000:00:13.1-3
[4295022.283000] spurious 8259A interrupt: IRQ7.
[4296173.332000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296173.332000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296331.622000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296331.622000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296409.909000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296409.909000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297316.923000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297316.923000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297331.084000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297331.084000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302278.131000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4302278.131000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302784.754000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4302784.754000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4302785.598000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4302785.598000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4308206.551000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4308206.551000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4310012.343000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4310012.343000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4310012.544000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4310012.544000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4310012.705000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4310012.705000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4310012.865000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4310012.865000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4310013.016000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4310013.016000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4310016.323000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4310016.323000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4310017.378000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4310017.378000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4316314.238000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4316314.238000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4320462.706000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4320462.706000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4321171.397000] usb 2-4: new full speed USB device using ohci_hcd and address 5[4321173.937000] Initializing USB Mass Storage driver...
[4321173.938000] scsi0 : SCSI emulation for USB Mass Storage devices
[4321173.941000] usb-storage: device found at 5
[4321173.941000] usb-storage: waiting for device to settle before scanning
[4321173.941000] usbcore: registered new driver usb-storage
[4321173.941000] USB Mass Storage support registered.
[4321178.942000]   Vendor: Casio     Model: QV DigitalCamera  Rev: 1000
[4321178.942000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[4321179.034000] usb-storage: device scan complete
[4321179.299000] SCSI device sda: 246016 512-byte hdwr sectors (126 MB)
[4321179.305000] sda: Write Protect is off
[4321179.305000] sda: Mode Sense: 00 46 02 00
[4321179.305000] sda: assuming drive cache: write through
[4321179.383000] SCSI device sda: 246016 512-byte hdwr sectors (126 MB)
[4321179.390000] sda: Write Protect is off
[4321179.390000] sda: Mode Sense: 00 46 02 00
[4321179.390000] sda: assuming drive cache: write through
[4321179.390000]  /dev/scsi/host0/bus0/target0/lun0: p1
[4321179.413000] Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0
[4321181.325000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4321453.446000] usb 2-4: USB disconnect, address 5
[4321454.484000] scsi0 (0:0): rejecting I/O to dead device
[4321540.540000] ndiswrapper (add_wep_key:644): adding encryption key 1 failed (C0010015)
[4321551.164000] wlan0: no IPv6 routers present
[4321638.693000] ndiswrapper (add_wep_key:644): adding encryption key 1 failed (C0010015)
[4323755.623000] usb 2-4: new full speed USB device using ohci_hcd and address 6[4323755.757000] scsi1 : SCSI emulation for USB Mass Storage devices
[4323755.759000] usb-storage: device found at 6
[4323755.759000] usb-storage: waiting for device to settle before scanning
[4323760.759000]   Vendor: Casio     Model: QV DigitalCamera  Rev: 1000
[4323760.759000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[4323760.796000] SCSI device sda: 246016 512-byte hdwr sectors (126 MB)
[4323760.804000] sda: Write Protect is off
[4323760.804000] sda: Mode Sense: 00 46 02 00
[4323760.804000] sda: assuming drive cache: write through
[4323760.841000] SCSI device sda: 246016 512-byte hdwr sectors (126 MB)
[4323760.846000] sda: Write Protect is off
[4323760.846000] sda: Mode Sense: 00 46 02 00
[4323760.846000] sda: assuming drive cache: write through
[4323760.846000]  /dev/scsi/host1/bus0/target0/lun0: p1
[4323760.865000] Attached scsi removable disk sda at scsi1, channel 0, id 0, lun 0
[4323760.870000] usb-storage: device scan complete
[4323762.580000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4323782.946000] usb 2-4: USB disconnect, address 6
[4323782.948000] scsi1 (0:0): rejecting I/O to device being removed
[4323782.948000] Buffer I/O error on device sda1, logical block 2
[4323782.948000] lost page write due to I/O error on sda1
[4323782.948000] scsi1 (0:0): rejecting I/O to device being removed
[4323782.948000] Buffer I/O error on device sda1, logical block 33
[4323782.948000] lost page write due to I/O error on sda1
[4323782.948000] scsi1 (0:0): rejecting I/O to device being removed
[4323782.948000] Buffer I/O error on device sda1, logical block 63
[4323782.948000] lost page write due to I/O error on sda1
[4323782.948000] scsi1 (0:0): rejecting I/O to device being removed
[4323782.948000] Buffer I/O error on device sda1, logical block 95
[4323782.948000] lost page write due to I/O error on sda1
[4323782.948000] scsi1 (0:0): rejecting I/O to device being removed
[4323782.948000] Buffer I/O error on device sda1, logical block 127
[4323782.948000] lost page write due to I/O error on sda1
[4323782.948000] scsi1 (0:0): rejecting I/O to device being removed
[4323782.948000] Buffer I/O error on device sda1, logical block 12095
[4323782.948000] lost page write due to I/O error on sda1
[4323782.948000] Buffer I/O error on device sda1, logical block 12096
[4323782.948000] lost page write due to I/O error on sda1
[4323782.948000] Buffer I/O error on device sda1, logical block 12097
[4323782.948000] lost page write due to I/O error on sda1
[4323782.948000] Buffer I/O error on device sda1, logical block 12098
[4323782.948000] lost page write due to I/O error on sda1
[4323782.948000] Buffer I/O error on device sda1, logical block 12099
[4323782.948000] lost page write due to I/O error on sda1
[4323783.135000] scsi1 (0:0): rejecting I/O to dead device
[4324505.336000] atkbd.c: Keyboard on isa0060/serio0 reports too many keys pressed.
[4324505.358000] atkbd.c: Keyboard on isa0060/serio0 reports too many keys pressed.
[4324651.795000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4324651.795000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4324726.919000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4324726.919000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4324727.100000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4324727.100000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.[/QUOTE]

Monitor Resolution is 1024x786. I have perfect images at TV, meaning colour, can see full desktop etc. just overlay elements like videos doesn't get viewed at tv. already tryed switching resoution to 800x600 or 640x480 without success.

---

### Post by pelle.k on 2006-02-12
Well, i can clearly see, your driver is NOT connected to the accesspoint, and for that matter your essid doesn't seem to be set. see for yourself, the first line of iwconfig wlan0 !

if you do "iwconfig wlan0 essid YOURESSID" it should set, otherwise there is something wrong. Try that and then look at the output of iwconfig wlan0.

tv-out doesn't work like that. if u use totem you could try to use tv-out as output. look around in the menus.

---

### Post by Traudel on 2006-02-13
just updated to dapper drake, got video from mediaplayer shown on tv, but whole picture is black and white now. wlan adater is recognized without ndiswarpper now, but still problems with connecting to accespoint :(

[QUOTE="iwconfig"]eth1      IEEE 802.11b/g  ESSID:"home"  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          Tx-Power=off
          RTS thr:off   Fragment thr:off[/QUOTE]
no clue, why acecess point shoud be invalid, cause essid is right. i try changing both to uppercase

---

### Post by pelle.k on 2006-02-15
hi traudel.
Happy to hear that you card is working "native" without ndiswrapper. ndiswrapper is a PITA most of the time.
Try "iwlist scanning". If your router (or whatever) isn't set up to be "hidden" you shold see it's accespoint address, amongst other things...
After that do (if wlan0 is your wireless network card) "iwconfig wlan0 ap YOURADDRESSHERE".

If it does work, then just do "dhclient wlan0"
Now then?

[edit]and i forgot to mention, your tv-out is probably black and white becauase you're feeding the tv with s-video instead of composite, OR the other way around. You should set your tv-system as well. an example is, i use PAL-G because i live in sweden. If you live in the US it would be NTSC-X (by x, i mean i don't know what exactly).
Look in your xorg.conf (nano /etc/X11/xorg.conf) to have a look on what setting you are currently using.[/edit]

---

