---
title: "hiddev missing for IR receiver"
date: 2007-07-13
forum: Apple Intel Users
---

### Post by kmand on 2007-07-13
I'm running Feisty

Linux maclinux 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux

on an Intel Mac Mini. I'm excepting a /dev/usb/hiddev? for the IR receiver, but there is no /dev/usb at all. There is a variety of /dev/usbdev* devices including 

# ls -l /dev/usbdev4.3_ep00
crw-rw---- 1 root root 254, 16 2007-07-13 00:04 /dev/usbdev4.3_ep00

which corresponds to the hardware since

# cat /sys/class/usb_endpoint/usbdev4.3_ep00/device/manufacturer
 Apple Computer, Inc.
# cat /sys/class/usb_endpoint/usbdev4.3_ep00/device/product 
IR Receiver

It looks to me like the usb device is not hooked up through the hiddev driver. The hiddev driver itslef is loaded

# dmesg |grep hiddev
[    6.436000] usbcore: registered new interface driver hiddev

What am I missing? Is it a udev rule?

---

### Post by kneip on 2007-07-16
Hej there

I've been trying to figure this out as well in order to use lirc 0.8.2 with it's macmini driver, but didn't find any hints by now. Have you come across a solution? For what it's worth, the usb device is found, but then it looks like it's discarded (from dmesg:)
```
[    4.536000] usb 4-2: new full speed USB device using uhci_hcd and address 3
[    4.716000] usb 4-2: configuration #1 chosen from 1 choice
[    5.224000] usb 4-2: USB disconnect, address 3
[    6.456000] usb 4-2: new full speed USB device using uhci_hcd and address 5
[    6.636000] usb 4-2: configuration #1 chosen from 1 choice

```

Nevertheless the hardware tool states it as IR Receiver with subdevice USB HID interface. lsusb gives no information. All this after I blacklisted appleir, which is loaded by default and creates /dev/input/event3 (which in turn is of no use to me, because it limits me to 6 different key codes).

Thanks for any help.

Kneip

---

### Post by kmand on 2007-07-22
I ultimately resolved this by rebuilding the kernel to fix a blacklist in 

drivers/usb/input/hid-core.c

commenting out

    { USB_VENDOR_ID_APPLE, USB_DEVICE_ID_APPLE_IRREMOTE, HID_QUIRK_IGNORE },

---

