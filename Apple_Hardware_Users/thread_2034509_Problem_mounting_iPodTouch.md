---
title: "Problem mounting iPodTouch"
date: 2012-07-28
forum: Apple Hardware Users
---

### Post by RicSG on 2012-07-28
Hi to everybody, 
I installed ubuntu 10.04 as single boot on my MacBookPro and all is gone right.

The only problem I have is to mount the iPod Touch. When i plug the usb the device start to recharge while, the OS do not recognize its presence.

From synaptic I see I have installed: libipoddevice0, libipod-cil, ipod libimobiledevice0, ifuse.

This is what i tried:

```
r@mbp:~$ lsusb | grep Apple
Bus 007 Device 003: ID 05ac:021b Apple, Inc. Internal Keyboard/Trackpad
Bus 007 Device 002: ID 05ac:8242 Apple, Inc. 
Bus 003 Device 003: ID 05ac:8205 Apple, Inc. Bluetooth HCI
Bus 002 Device 002: ID 05ac:8502 Apple, Inc. Built-in iSight
Bus 001 Device 006: ID 05ac:1293 Apple, Inc. 
``````
r@mbp:~$ dmesg | grep usb
[    0.350190] usbcore: registered new interface driver usbfs
[    0.350190] usbcore: registered new interface driver hub
[    0.350190] usbcore: registered new device driver usb
[    0.470147] usb usb1: configuration #1 chosen from 1 choice
[    0.500266] usb usb2: configuration #1 chosen from 1 choice
[    0.500742] usb usb3: configuration #1 chosen from 1 choice
[    0.500999] usb usb4: configuration #1 chosen from 1 choice
[    0.501235] usb usb5: configuration #1 chosen from 1 choice
[    0.501464] usb usb6: configuration #1 chosen from 1 choice
[    0.501706] usb usb7: configuration #1 chosen from 1 choice
[    0.902558] usb 2-4: new high speed USB device using ehci_hcd and address 2
[    1.100317] usb 2-4: configuration #1 chosen from 1 choice
[    1.570050] usb 3-1: new full speed USB device using uhci_hcd and address 2
[    1.761834] usb 3-1: configuration #1 chosen from 1 choice
[    2.042552] usb 7-1: new low speed USB device using uhci_hcd and address 2
[    2.223825] usb 7-1: configuration #1 chosen from 1 choice
[    2.512559] usb 7-2: new full speed USB device using uhci_hcd and address 3
[    2.706846] usb 7-2: configuration #1 chosen from 1 choice
[   15.416733] input: appletouch as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.1/input/input6
[   15.416838] usbcore: registered new interface driver appletouch
[   15.426164] input: Built-in iSight as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4:1.0/input/input7
[   15.426223] usbcore: registered new interface driver uvcvideo
[   15.487341] usbcore: registered new interface driver hiddev
[   15.505694] input: HID 05ac:1000 as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0/input/input9
[   15.505812] generic-usb 0003:05AC:1000.0001: input,hidraw0: USB HID v1.11 Keyboard [HID 05ac:1000] on usb-0000:00:1a.0-1/input0
[   15.641945] input: HID 05ac:1000 as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.1/input/input10
[   15.642052] generic-usb 0003:05AC:1000.0002: input,hidraw1: USB HID v1.11 Mouse [HID 05ac:1000] on usb-0000:00:1a.0-1/input1
[   15.642197] usbcore: registered new interface driver usbhid
[   15.642199] usbhid: v2.6:USB HID core driver
[   15.679093] apple 0003:05AC:8242.0003: hiddev96,hidraw2: USB HID v1.11 Device [Apple Computer, Inc. IR Receiver] on usb-0000:00:1d.2-1/input0
[   15.682998] input: Apple Computer Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/input/input11
[   15.683077] apple 0003:05AC:021B.0004: input,hidraw3: USB HID v1.11 Keyboard [Apple Computer Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input0
[   15.686738] input: Apple Computer Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.2/input/input12
[   15.686825] apple 0003:05AC:021B.0005: input,hidraw4: USB HID v1.11 Device [Apple Computer Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input2
[   15.737107] usb 3-1: usbfs: USBDEVFS_CONTROL failed cmd hid2hci rqt 64 rq 0 len 0 ret -84
[   16.060076] usb 3-1: USB disconnect, address 2
[   17.470038] usb 3-1: new full speed USB device using uhci_hcd and address 3
[   17.672863] usb 3-1: configuration #1 chosen from 1 choice
[   17.685661] usbcore: registered new interface driver btusb
[ 3612.370182] usb 1-2: new high speed USB device using ehci_hcd and address 4
[ 3612.524772] usb 1-2: configuration #1 chosen from 1 choice
[ 3612.654527] usbcore: registered new interface driver usb-storage
[ 3612.655122] usb-storage: device found at 4
[ 3612.655124] usb-storage: waiting for device to settle before scanning
[ 3617.653067] usb-storage: device scan complete
[ 3618.911034] usb 1-2: USB disconnect, address 4
[ 3638.780166] usb 1-2: new high speed USB device using ehci_hcd and address 5
[ 3638.944712] usb 1-2: configuration #1 chosen from 1 choice
[ 3638.945995] usb-storage: device found at 5
[ 3638.946000] usb-storage: waiting for device to settle before scanning
[ 3643.943130] usb-storage: device scan complete
[ 4484.062715] usb 1-2: USB disconnect, address 5
[ 4508.480196] usb 2-1: new high speed USB device using ehci_hcd and address 5
[ 4508.637259] usb 2-1: configuration #1 chosen from 3 choices
[ 4525.628562] usb 2-1: USB disconnect, address 5
[ 5834.550187] usb 1-2: new high speed USB device using ehci_hcd and address 6
[ 5834.712064] usb 1-2: configuration #1 chosen from 3 choices

```Do you have any suggetion to mount the iPod Touch??

Best
R

---

