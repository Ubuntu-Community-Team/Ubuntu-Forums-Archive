---
title: "Ubuntu 10.4 on Mac logging out frequently"
date: 2010-09-14
forum: Apple Hardware Users
---

### Post by ckkashyap on 2010-09-14
I installed Ubuntu 10.4 64bit on my mac - hw.model: MacBookPro4,1

I noticed that every now and then, I get logged out and loose the entire session and get back to the login screen

I notice this in dmesg very frequently - 

Sep 14 06:57:58 ckk-laptop kernel: [36210.040308] usb 7-2: USB
disconnect, address 96
Sep 14 06:57:58 ckk-laptop kernel: [36210.470217] usb 7-2: new full
speed USB device using uhci_hcd and address 97
Sep 14 06:57:59 ckk-laptop kernel: [36210.664618] usb 7-2:
configuration #1 chosen from 1 choice
Sep 14 06:57:59 ckk-laptop kernel: [36210.677769] input: Apple, Inc.
Apple Internal Keyboard / Trackpad as
/devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/input/input199
Sep 14 06:57:59 ckk-laptop kernel: [36210.678008] apple
0003:05AC:0230.00C0: input,hidraw0: USB HID v1.11 Keyboard [Apple,
Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input0
Sep 14 06:57:59 ckk-laptop kernel: [36211.180557] apple
0003:05AC:0230.00C1: hidraw1: USB HID v1.11 Device [Apple, Inc. Apple
Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input1
Sep 14 06:57:59 ckk-laptop kernel: [36211.182465] input: bcm5974 as
/devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.2/input/input200


I am not sure if they are related though

---

