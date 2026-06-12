---
title: "How To Install Webcam Drivers?"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by rookshop on 2008-01-14
Hi, 

I just downloaded the drivers for my webcam from the manufacturers website. All I got was the file "snxcam.o" with no installation instructions. Can you please tell me what to do with this file so that my webcam will finally work?

Thanks in advance,
Rookshop

---

### Post by wieman01 on 2008-01-14
What webcam have you got? 

Please plug it in and post the results of:
> dmesg
Usually you have to put driver files here:
> /lib/firmware
But I don't really know in your case. Could you also post the link to that specific website?

---

### Post by rookshop on 2008-01-14
Here it is:
```
[   17.600000] serio: Synaptics pass-through port at isa0060/serio1/input0
[   17.644000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   17.788000] cs: IO port probe 0x100-0x3af: clean.
[   17.788000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   17.792000] cs: IO port probe 0x820-0x8ff: clean.
[   17.792000] cs: IO port probe 0xc00-0xcf7: clean.
[   17.792000] cs: IO port probe 0xa00-0xaff: clean.
[   17.952000] ACPI: PCI Interrupt 0000:00:1b.0[B] -> GSI 17 (level, low) -> IRQ 21
[   17.952000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   18.520000] lp: driver loaded but no devices found
[   18.592000] Adding 1485972k swap on /dev/sda5.  Priority:-1 extents:1 across:1485972k
[   18.936000] EXT3 FS on sda1, internal journal
[   19.348000] hda_intel: azx_get_response timeout, switching to polling mode...
[   20.416000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   20.416000] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   20.428000] ACPI: ACPI Dock Station Driver 
[   20.428000] ACPI: \_SB_.PCI0.IDE0.PRIM.MSTR: found ejectable bay
[   20.428000] ACPI: \_SB_.PCI0.IDE0.PRIM.MSTR: Adding notify handler
[   20.428000] ACPI: Bay [\_SB_.PCI0.IDE0.PRIM.MSTR] Added
[   20.428000] ACPI: \_SB_.PCI0.SATA.SCND.MSTR: found ejectable bay
[   20.428000] ACPI: \_SB_.PCI0.SATA.SCND.MSTR: Adding notify handler
[   20.428000] ACPI: Error installing bay notify handler
[   20.428000] ACPI: Bay [\_SB_.PCI0.SATA.SCND.MSTR] Added
[   20.476000] ACPI: Battery Slot [BAT0] (battery present)
[   20.564000] input: Power Button (FF) as /class/input/input4
[   20.564000] ACPI: Power Button (FF) [PWRF]
[   20.564000] input: Lid Switch as /class/input/input5
[   20.564000] ACPI: Lid Switch [LID]
[   20.564000] input: Sleep Button (CM) as /class/input/input6
[   20.564000] ACPI: Sleep Button (CM) [SLPB]
[   20.676000] ACPI: AC Adapter [AC] (on-line)
[   22.780000] ppdev: user-space parallel port driver
[   22.944000] audit(1200234854.246:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4959 profile="/usr/sbin/cupsd"
[   23.216000] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   23.436000] input: TPPS/2 IBM TrackPoint as /class/input/input7
[   25.976000] apm: BIOS not found.
[   27.068000] thinkpad_acpi: ThinkPad ACPI Extras v0.14
[   27.068000] thinkpad_acpi: http://ibm-acpi.sf.net/
[   27.068000] thinkpad_acpi: ThinkPad EC firmware 7CHT14WW-1.02
[   27.072000] thinkpad_acpi: another device driver is already handling bay events
[   27.072000] thinkpad_acpi: disabling subdriver bay
[   27.220000] Failure registering capabilities with primary security module.
[   27.456000] Bluetooth: Core ver 2.11
[   27.456000] NET: Registered protocol family 31
[   27.456000] Bluetooth: HCI device and connection manager initialized
[   27.456000] Bluetooth: HCI socket layer initialized
[   27.484000] Bluetooth: L2CAP ver 2.8
[   27.484000] Bluetooth: L2CAP socket layer initialized
[   27.592000] Bluetooth: RFCOMM socket layer initialized
[   27.592000] Bluetooth: RFCOMM TTY layer initialized
[   27.592000] Bluetooth: RFCOMM ver 1.8
[   31.960000] [drm] Initialized drm 1.1.0 20060810
[   32.148000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 20
[   32.148000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   47.220000] UDF-fs: Partition marked readonly; forcing readonly mount
[   47.268000] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'My Disc', timestamp 2005/09/14 11:26 (114a)
[   56.428000] NET: Registered protocol family 17
[   71.748000] NET: Registered protocol family 10
[   71.748000] lo: Disabled Privacy Extensions
[   71.748000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   82.580000] ath0: no IPv6 routers present
[ 7850.972000] wifi0: rx FIFO overrun; resetting
[27294.336000] ADDRCONF(NETDEV_UP): ath0: link is not ready
[27304.184000] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[27321.108000] ath0: no IPv6 routers present
[38146.832000] ADDRCONF(NETDEV_UP): ath0: link is not ready
[38156.768000] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[38170.456000] ath0: no IPv6 routers present
[38260.040000] ADDRCONF(NETDEV_UP): ath0: link is not ready
[38269.692000] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[38280.160000] ath0: no IPv6 routers present
[38314.656000] ADDRCONF(NETDEV_UP): ath0: link is not ready
[38324.444000] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[38335.428000] ath0: no IPv6 routers present
[38372.188000] ADDRCONF(NETDEV_UP): ath0: link is not ready
[62840.944000] ADDRCONF(NETDEV_UP): ath0: link is not ready
[62850.536000] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[62866.352000] ath0: no IPv6 routers present
[65249.640000] usb 3-1: new full speed USB device using uhci_hcd and address 2
[65249.800000] usb 3-1: configuration #1 chosen from 1 choice
[65250.588000] Linux video capture interface: v2.00
[65250.700000] sn9c102: V4L2 driver for SN9C1xx PC Camera Controllers v1:1.44
[65250.704000] usb 3-1: SN9C120 PC Camera Controller detected (vid:pid 0x0C45:0x613A)
[65250.804000] usb 3-1: No supported image sensor detected for this bridge
[65250.804000] usbcore: registered new interface driver sn9c102
```

There was no other installation instructions on the manufacturers website. Just a .rar file containing snxcam.o

---

### Post by zuzuzzzip on 2008-01-14
maybe this might help:
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

---

### Post by wieman01 on 2008-01-14
> **rookshop said:**
> There was no other installation instructions on the manufacturers website. Just a .rar file containing snxcam.o
Please post the link if possible.

---

### Post by Capslock118 on 2008-01-15
I am getting the same error but with this line instead:

```

usb 2-2: SN9C105 PC Camera Controller detected (vid:pid 0x0C45:0x60FE)

```

If anyone has information that does not take me through a loop of threads I would appreciate it. I will document what I do when my camera finally works and let you know.

---

### Post by Capslock118 on 2008-01-15
Here is a full report of my syslogs if this helps anyone:

```

Jan 15 12:54:36 joelandally kernel: [ 4444.190650] usb 1-2: new full speed USB device using ohci_hcd and address 4
Jan 15 12:54:37 joelandally NetworkManager: <debug> [1200419677.114401] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_c45_60fe_noserial'). 
Jan 15 12:54:37 joelandally kernel: [ 4444.302861] usb 1-2: configuration #1 chosen from 1 choice
Jan 15 12:54:37 joelandally kernel: [ 4444.306123] usb 1-2: SN9C105 PC Camera Controller detected (vid:pid 0x0C45:0x60FE)
Jan 15 12:54:37 joelandally NetworkManager: <debug> [1200419677.328731] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial'). 
Jan 15 12:54:37 joelandally kernel: [ 4444.477750] usb 1-2: No supported image sensor detected for this bridge
Jan 15 12:54:37 joelandally NetworkManager: <debug> [1200419677.499082] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_0'). 
Jan 15 12:54:37 joelandally NetworkManager: <debug> [1200419677.586525] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_c45_60fe_noserial_if2'). 
Jan 15 12:54:37 joelandally NetworkManager: <debug> [1200419677.612068] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_0_alsa_capture_0'). 
Jan 15 12:54:37 joelandally NetworkManager: <debug> [1200419677.636740] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_0_oss_pcm_0'). 
Jan 15 12:54:37 joelandally NetworkManager: <debug> [1200419677.661871] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_0_oss_pcm_0_0'). 
Jan 15 12:54:37 joelandally NetworkManager: <debug> [1200419677.688174] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_0_oss_mixer__1'). 
Jan 15 12:54:37 joelandally NetworkManager: <debug> [1200419677.744181] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_c45_60fe_noserial_usbraw'). 
Jan 15 12:54:37 joelandally NetworkManager: <debug> [1200419677.772590] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_0_alsa_control__1'). 

```

---

### Post by trance4life1886 on 2008-01-16
hello!  i have a kinstone ks-188 webcam and i want to use it on ubuntu 7.10 cuz im tired of MS .. so if anyone can halp that would be cool !

---

