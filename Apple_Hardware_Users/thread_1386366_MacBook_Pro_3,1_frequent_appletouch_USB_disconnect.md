---
title: "MacBook Pro 3,1 frequent appletouch USB disconnects?"
date: 2010-01-20
forum: Apple Hardware Users
---

### Post by coreyoconnor on 2010-01-20
Hi all,

I have an MacBook Pro 3,1 running Karmic ( 9.10 ) 64bit. The kernel is 2.6.32 patched to use the BFS scheduler. I am having issues with the touchpad and the keyboard. On occasion they stop working. It is possible that I have damaged hardware. However I would like to see if any other users report similar issues before blaming the HW. At the end of this message is what dmesg reports when this occurs.

Often, before the touchpad and keyboard completely stop working they appear to stutter. They work fine then stop responding briefly then start working again. 

dmesg usually reports a sequence like the following:
```

[22717.854544] appletouch: OVERFLOW with data length 64, actual length is 0
[22717.954191] hub 7-0:1.0: port 2 disabled by hub (EMI?), re-enabling...
[22717.954200] usb 7-2: USB disconnect, address 9
[22717.974536] input: appletouch disconnected
[22718.184145] usb 7-2: new full speed USB device using uhci_hcd and address 10
[22718.564161] usb 7-2: configuration #1 chosen from 1 choice
[22718.574448] input: Apple Computer Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/input/input33
[22718.574554] apple 0003:05AC:021A.0014: input,hidraw1: USB HID v1.11 Keyboard [Apple Computer Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input0
[22718.579377] appletouch: Geyser mode initialized.
[22718.579441] input: appletouch as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.1/input/input34
[22718.595369] input: Apple Computer Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.2/input/input35
[22718.595444] apple 0003:05AC:021A.0015: input,hidraw2: USB HID v1.11 Device [Apple Computer Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input2
[22775.126251] input: appletouch disconnected
[22775.228118] usb 7-2: reset full speed USB device using uhci_hcd and address 10
[22775.375300] appletouch: Geyser mode initialized.
[22775.375402] input: appletouch as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.1/input/input36
[22777.704261] usb 7-2: USB disconnect, address 10
[22777.727277] input: appletouch disconnected
[22777.939191] usb 7-2: new full speed USB device using uhci_hcd and address 11

```

---

### Post by coreyoconnor on 2010-01-21
Looks like I'm not the only one at least :-) :-(:
[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/395568]("https://bugs.launchpad.net/ubuntu/+source/udev/+bug/395568")

---

### Post by carpy on 2010-02-11
If you want a currently open bug, try this one:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/243707](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/243707)

Throw your hat in the ring and hope with the rest of us.  I'm getting pretty convinced it's not just hardware failure.  Do you also lose wireless network once in a while for apparently not reason?

---

