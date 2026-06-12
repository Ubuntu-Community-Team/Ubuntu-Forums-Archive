---
title: "USB devices interface location"
date: 2005-07-03
forum: Absolute Beginner Talk
---

### Post by MrSandman on 2005-07-03
how do i tell which node my usb device is connecting to? i am trying to get my eartmate to work under gpsdrive but i dont know the interface location

lsusb shows

us 005 Device 001: ID 0000:0000
Bus 004 Device 005: ID 0461:4d03 Primax Electronics, Ltd Kensington Mouse-in-a-box
Bus 004 Device 004: ID 1163:0200 DeLorme Publishing, Inc.
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

and dmesg | grep usb shows

dmesg | grep usb
usbcore: registered new driver usbfs
usbcore: registered new driver hub
usb 4-2: new low speed USB device using uhci_hcd and address 2
usb 4-2: device descriptor read/64, error -71
usb 4-2: new low speed USB device using uhci_hcd and address 3
usbcore: registered new driver hiddev
input: USB HID v1.00 Mouse [ARROW STRONG USB 3D Mouse] on usb-0000:00:1d.3-2
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.0:USB HID core driver
usb 4-1: new full speed USB device using uhci_hcd and address 4
hiddev96: USB HID v1.00 Device [DeLorme Publishing DeLorme USB Earthmate      ] on usb-0000:00:1d.3-1
drivers/usb/input/hid-core.c: input irq status -84 received
drivers/usb/input/hid-core.c: input irq status -84 received
drivers/usb/input/hid-core.c: input irq status -84 received
usb 4-2: USB disconnect, address 3
usb 4-2: new low speed USB device using uhci_hcd and address 5
usb 4-2: device descriptor read/64, error -71
input: USB HID v1.00 Mouse [ARROW STRONG USB 3D Mouse] on usb-0000:00:1d.3-2


so its recognizing the earthmate, but how do i connect to use the data?? THANKS

---

### Post by Error_Msg on 2005-07-04
Have you tried gpstrans? It will ask you for the port tho.

E_M

---

