---
title: "How to mount a USB Mobile Phone...?"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by Hopeless on 2007-08-13
Hi,

I would like to mount my mobile...

I plug it in and don't get anything...here is the Messsage  logs...

Aug 13 16:55:54 lotus kernel: [88467.125855] usb 1-1: USB disconnect, address 6
Aug 13 17:00:12 lotus kernel: [88724.819629] usb 1-1: new full speed USB device using uhci_hcd and address 7
Aug 13 17:00:12 lotus kernel: [88724.990903] usb 1-1: configuration #1 chosen from 1 choice
Aug 13 17:00:12 lotus kernel: [88724.993930] cdc_acm 1-1:1.0: ttyACM0: USB ACM device

it's CDMA SPH-V8450 Samsung...BitPim dosen't pick it up...

lsusb...

Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 007: ID 04e8:6601 Samsung Electronics Co., Ltd Z100 Mobile Phone
Bus 001 Device 005: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000  


Any ideas?

---

### Post by Kobalt on 2007-08-13
Unfortunatey, connecting through USB a cell phone to Ubuntu provides rather random effects. And I don't recall reading somewhere it either worked out of the box or worked at all... 
If you can I advise you to use bluetooth to transfer files between your cell phone and your computer.

---

