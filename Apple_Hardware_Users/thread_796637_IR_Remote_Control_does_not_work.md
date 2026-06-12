---
title: "IR Remote Control does not work"
date: 2008-05-16
forum: Apple Hardware Users
---

### Post by netAction on 2008-05-16
Hello!

In Gutsy everything worked fine. Now I have Kubuntu Hardy, and the remote of my white 20" Intel iMac does not do a thing.

$ dmesg:
[  542.645361] hidraw0: USB HID v1.11 Device [Apple Computer, Inc. IR Receiver] on usb-0000:00:1d.3-2

$ lsusb:
Bus 004 Device 010: ID 05ac:8240 Apple Computer, Inc. IR Receiver [build-in]

I searched for hours, but nothing helped.
Thomas

---

### Post by cyberdork33 on 2008-05-16
Someone had a 24" iMac and got it to work in a thread in the archives:
[http://ubuntuforums.org/showthread.php?t=607797](http://ubuntuforums.org/showthread.php?t=607797)

You can also try the MacbookPro wiki instructions:
[https://help.ubuntu.com/community/MacBookPro#head-1c8a17fe0bebfc24d30955e34266151826a45e83](https://help.ubuntu.com/community/MacBookPro#head-1c8a17fe0bebfc24d30955e34266151826a45e83)

---

### Post by netAction on 2008-05-16
The first URL deals with another remote, I think.
I do not have to change the source code therefore I do not have to compile anything.

The second URL does not work, too:
```
$ sudo /usr/bin/irexec
irexec: could not connect to socket
irexec: Connection refused
```

```
$ sudo lsinput
```
I can not see any "Remote".

I tried modprobe appleir, rmmod usbhid. And then I reconnected the keyboard.

```
$ dmesg
[ 7699.280483] input: Apple Mac mini infrared remote control driver as /devices/pci0000:00/0000:00:1d.3/usb4/4-2/4-2:1.0/input/input16
[ 7699.345490] input: failed to attach handler kbd to device input16, error: -5
[ 7699.357544] usbcore: registered new interface driver appleir
[ 7699.357558] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/mactel/appleir.c: v1.1:USB Apple MacMini IR Receiver driver
[ 7711.259946] usbcore: deregistering interface driver usbhid
[ 7711.404402] usbcore: deregistering interface driver hiddev
[ 7715.314244] usb 2-1: USB disconnect, address 9
[ 7715.314253] usb 2-1.1: USB disconnect, address 10
[ 7715.314620] usb 2-1.3: USB disconnect, address 11
[ 7722.045004] usb 2-1: new full speed USB device using uhci_hcd and address 12
[ 7722.220857] usb 2-1: configuration #1 chosen from 1 choice
[ 7722.223729] hub 2-1:1.0: USB hub found
[ 7722.225677] hub 2-1:1.0: 3 ports detected
[ 7722.537079] usb 2-1.1: new low speed USB device using uhci_hcd and address 13
[ 7722.667017] usb 2-1.1: configuration #1 chosen from 1 choice
[ 7722.872425] usb 2-1.3: new full speed USB device using uhci_hcd and address 14
[ 7723.014320] usb 2-1.3: configuration #1 chosen from 1 choice
[ 7723.021156] usbcore: registered new interface driver hiddev
[ 7723.034513] input: PS/2+USB Mouse as /devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1.1/2-1.1:1.0/input/input17
[ 7723.082984] input,hidraw0: USB HID v1.11 Mouse [PS/2+USB Mouse] on usb-0000:00:1d.1-1.1
[ 7723.088248] input: Mitsumi Electric Apple Extended USB Keyboard as /devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1.3/2-1.3:1.0/input/input18
[ 7723.130961] input,hidraw1: USB HID v1.10 Keyboard [Mitsumi Electric Apple Extended USB Keyboard] on usb-0000:00:1d.1-1.3
[ 7723.138013] input: Mitsumi Electric Apple Extended USB Keyboard as /devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1.3/2-1.3:1.1/input/input19
[ 7723.174848] input,hidraw2: USB HID v1.10 Device [Mitsumi Electric Apple Extended USB Keyboard] on usb-0000:00:1d.1-1.3
[ 7723.174880] usbcore: registered new interface driver usbhid
[ 7723.174887] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
```

---

