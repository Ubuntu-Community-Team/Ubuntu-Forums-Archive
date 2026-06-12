---
title: "USB Keyboard/Mouse issues on restart..."
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by scottness on 2007-03-16
Whenever I restart my system and boot into Ubuntu Edgy, my USB keyboard and mouse are not responding correctly.  The keyboard is slow to respond, and when it does finally respond, it will lock on one key.  My temporary fix for this problem has been to unplug the keyboard and the mouse from their USB ports and move them to another open USB port.  This resets the connect and all is well...until I need to reboot (generally if I'm booting into my Windows partition).

My error output from the system log is:
 > Mar 16 22:25:48 sbevill-desktop kernel: [17188675.932000] usb 1-2: reset low speed USB device using uhci_hcd and address 5
Mar 16 22:25:57 sbevill-desktop kernel: [17188684.692000] usb 1-2: reset low speed USB device using uhci_hcd and address 5
Mar 16 22:25:59 sbevill-desktop kernel: [17188686.876000] usb 1-2: reset low speed USB device using uhci_hcd and address 5
Mar 16 22:26:02 sbevill-desktop kernel: [17188689.516000] usb 1-2: reset low speed USB device using uhci_hcd and address 5

This takes up at least a few pages in my syslog.  After I disconnect the USB keyboard and mouse, I get this message:

> Mar 16 22:26:03 sbevill-desktop kernel: [17188690.480000] usb 1-2: USB disconnect, address 5
Mar 16 22:26:05 sbevill-desktop kernel: [17188693.156000] usb 2-1: new low speed USB device using uhci_hcd and address 2
Mar 16 22:26:05 sbevill-desktop kernel: [17188693.328000] usb 2-1: configuration #1 chosen from 1 choice
Mar 16 22:26:05 sbevill-desktop kernel: [17188693.348000] input: Logitech USB Mouse as /class/input/input5
Mar 16 22:26:05 sbevill-desktop kernel: [17188693.352000] input: USB HID v1.10 Mouse [Logitech USB Mouse] on usb-0000:00:1d.1-1
Mar 16 22:26:06 sbevill-desktop kernel: [17188693.756000] usb 1-1: USB disconnect, address 4
Mar 16 22:26:08 sbevill-desktop kernel: [17188695.620000] usb 2-2: new low speed USB device using uhci_hcd and address 3
Mar 16 22:26:08 sbevill-desktop kernel: [17188695.896000] usb 2-2: configuration #1 chosen from 1 choice
Mar 16 22:26:08 sbevill-desktop kernel: [17188695.956000] input: Chicony Saitek Eclipse Keyboard as /class/input/input6
Mar 16 22:26:08 sbevill-desktop kernel: [17188695.956000] input: USB HID v1.11 Keyboard [Chicony Saitek Eclipse Keyboard] on usb-0000:00:1d.1-2
Mar 16 22:26:08 sbevill-desktop kernel: [17188696.068000] input: Chicony Saitek Eclipse Keyboard as /class/input/input7
Mar 16 22:26:08 sbevill-desktop kernel: [17188696.068000] input,hiddev96: USB HID v1.11 Device [Chicony Saitek Eclipse Keyboard] on usb-0000:00:1d.1-2

Any ideas on how to find a more permanent fix for this problem?  I've tried to adjust the settings in the BIOS on startup, but that seems to have had no effect.  Thanks in advance.

---

