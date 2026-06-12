---
title: "USB Ethernet adapter"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by leo_br on 2008-01-12
Hello all,

i have the following problem: When I boot up my laptop my USB card doesn't work, but after disconnect and connect it again it works perfectly. 
Any ideas how to make it work properly?
Here is my dmesg after the boot, disconnect and connect again

```


:~$ dmesg |grep usb
[   48.176674] usbcore: registered new interface driver usbfs
[   48.176758] usbcore: registered new interface driver hub
[   48.176827] usbcore: registered new device driver usb
[    3.016000]  sda: sda1 sda2 sda3 <<6>usb usb1: configuration #1 chosen from 1 choice
[    3.212000] usb usb2: configuration #1 chosen from 1 choice
[    3.388000] usb usb3: configuration #1 chosen from 1 choice
[    3.908000] usb 3-2: new high speed USB device using ehci_hcd and address 2
[    4.052000] usb 3-2: configuration #1 chosen from 1 choice
[    4.540000] usb 2-3: new low speed USB device using ohci_hcd and address 2
[    4.752000] usb 2-3: configuration #1 chosen from 1 choice
[   16.876000] usbcore: registered new interface driver hiddev
[   16.916000] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:03.1-3
[   16.916000] usbcore: registered new interface driver usbhid
[   16.916000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   19.052000] usbcore: registered new interface driver pegasus
[   88.952000] usb 3-2: USB disconnect, address 2
[   93.856000] usb 3-2: new high speed USB device using ehci_hcd and address 4
[   93.992000] usb 3-2: configuration #1 chosen from 1 choice

```

and my lsusb if somebody need it:

```

~$ lsusb
Bus 003 Device 004: ID 07a6:8515 ADMtek, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  


```

---

### Post by njparton on 2008-01-14
Try booting without it plugged in and then insert it after you're up and running?

---

### Post by leo_br on 2008-01-14
Thanks for your reply!

It will for sure work, but I wanted to just turn on my computer and have it connected without having to plug/unplug my net adapter every time

---

### Post by swoll1980 on 2008-01-14
if you used ndiswrapper just do a sudo gedit  /etc/module add ndiswrapper to the file then save

---

### Post by swoll1980 on 2008-01-14
if not you would have to find out the name of the module it's using and add that to the list

---

### Post by leo_br on 2008-01-14
I have already tried this and added ¨pegasus¨ to the suggested file without succes. It's the module I suppose it is using from what I understood in my dmesg

How can I know which module it is using?

---

