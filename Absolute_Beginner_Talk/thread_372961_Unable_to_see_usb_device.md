---
title: "Unable to see usb device"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by JeremyLaurenson on 2007-02-28
Hi all,

I have a USB PowerLinc external USB X10 transmitter connected.

I see it connect when I tail /var/log/messages:
Feb 28 19:25:04 ubuntu01 kernel: [42950088.210000] usb 1-2: new low speed USB device using ohci_hcd and address 3
Feb 28 19:25:05 ubuntu01 kernel: [42950088.460000] hiddev96: USB HID v1.00 Device [SmartHome SmartHome PowerLinc USB] on usb-0000:00:0f.2-2

But I do not see a /dev/usb entry... How should I be mounting this?

PS: My x10 driver is looking for it in /dev/usb/hiddev0 
modprobe x10 
/usr/sbin/plusbd -device /dev/usb/hiddev0 
/usr/sbin/x10logd 


Feb 28 19:18:16 ubuntu01 kernel: [42949680.170000] x10: $Id: dev.c,v 1.23 2006/03/29 02:33:23 root Exp root $
Feb 28 19:18:16 ubuntu01 kernel: [42949680.170000] x10: X10 driver successfully loaded
Feb 28 19:19:00 ubuntu01 plusbd[4356]: starting. api-device=/dev/x10/.api, pidfile=/var/run/x10d.pid
Feb 28 19:19:00 ubuntu01 plusbd[4356]: Successfully opened X10 API device /dev/x10/.api
Feb 28 19:19:01 ubuntu01 plusbd[4357]: Transmit thread starting
Feb 28 19:19:01 ubuntu01 plusbd[4357]: Error opening /dev/usb/hiddev0 (No such file or directory)

---

### Post by JeremyLaurenson on 2007-02-28
Got it...

/usr/sbin/plusbd -device /dev/hiddev0

All works.

---

