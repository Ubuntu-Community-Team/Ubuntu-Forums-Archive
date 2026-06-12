---
title: "Can't mount media devices at all."
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by ratbagradio on 2007-07-23
I need to mount a few devices in my new install of Edgy. But despite an easy history on this machine running XP  the devices won't mount and nothing is recognised   via the usb port except my digital camera.

i know what the read outs ays but these ports have worked fine for yonks!

My items: after exploring the problem with code
> dmesg | tail


[B]
USB stick:[/B]

> [17183831.688000] usb 1-2: new full speed USB device using uhci_hcd and address 5
[17183832.096000] usb 1-2: device not accepting address 5, error -71
[17183857.584000] usb 4-2: new high speed USB device using ehci_hcd and address 23
[17183858.456000] hub 4-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[17183858.568000] usb 4-2: new high speed USB device using ehci_hcd and address 24
[17183859.440000] hub 4-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[17183859.552000] usb 4-2: new high speed USB device using ehci_hcd and address 25
[17183859.960000] usb 4-2: device not accepting address 25, error -71
[17183860.072000] usb 4-2: new high speed USB device using ehci_hcd and address 26
[17183860.480000] usb 4-2: device not accepting address 26, error -71




**Iriver T30 Mp3 media player**
> 
[17183860.072000] usb 4-2: new high speed USB device using ehci_hcd and address 26
[17183860.480000] usb 4-2: device not accepting address 26, error -71
[17184841.644000] usb 4-1: new high speed USB device using ehci_hcd and address 27
[17184842.516000] hub 4-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[17184842.628000] usb 4-1: new high speed USB device using ehci_hcd and address 28
[17184843.500000] hub 4-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[17184843.612000] usb 4-1: new high speed USB device using ehci_hcd and address 29
[17184844.020000] usb 4-1: device not accepting address 29, error -71
[17184844.132000] usb 4-1: new high speed USB device using ehci_hcd and address 30
[17184844.540000] usb 4-1: device not accepting address 30, error -71
[B]
iRiver IFP Mp3 media player [/B]
> 
[17184844.132000] usb 4-1: new high speed USB device using ehci_hcd and address 30
[17184844.540000] usb 4-1: device not accepting address 30, error -71
[17185076.004000] usb 4-1: new high speed USB device using ehci_hcd and address 31
[17185076.876000] hub 4-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[17185076.988000] usb 4-1: new high speed USB device using ehci_hcd and address 32
[17185077.860000] hub 4-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[17185077.972000] usb 4-1: new high speed USB device using ehci_hcd and address 33
[17185078.380000] usb 4-1: device not accepting address 33, error -71
[17185078.492000] usb 4-1: new high speed USB device using ehci_hcd and address 34
[17185078.900000] usb 4-1: device not accepting address 34, error

---

### Post by ratbagradio on 2007-07-23
If I try thsi work around I get(after dpoing soem ea fiddles earlier)

> ratbagradio@Ratbag:~$ sudo mkdir /media/irivert30
Password:
mkdir: cannot create directory `/media/irivert30': File exists

ratbagradio@Ratbag:~$ sudo mount -t vfat /dev/sda /media/irivert30
mount: special device /dev/sda does not exist
ratbagradio@Ratbag:~$ 


So i have the directory (for my T30) but can't get it to talk the talk...

---

