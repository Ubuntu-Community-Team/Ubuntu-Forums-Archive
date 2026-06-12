---
title: "Long timeout in boot on MBP5,1/Maverick"
date: 2010-12-13
forum: Apple Hardware Users
---

### Post by SwedishWings on 2010-12-13
This has been bugging me since Karmic: I have a very long (~20 seconds) delay in the boot process as the dmesg log illustrates:

```
[    4.068353] usb 2-2.3: new low speed USB device using ehci_hcd and address 5
[    4.211866] input:   USB Keyboard as /devices/pci0000:00/0000:00:06.1/usb2/2-2/2-2.3/2-2.3:1.0/input/input5
[    4.212140] generic-usb 0003:09DA:0260.0005: input,hidraw3: USB HID v1.10 Keyboard [  USB Keyboard] on usb-0000:00:06.1-2.3/input0
[    4.231772] input:   USB Keyboard as /devices/pci0000:00/0000:00:06.1/usb2/2-2/2-2.3/2-2.3:1.1/input/input6
[    4.231998] generic-usb 0003:09DA:0260.0006: input,hidraw4: USB HID v1.10 Device [  USB Keyboard] on usb-0000:00:06.1-2.3/input1
[    4.310113] usb 4-1.1: new full speed USB device using ohci_hcd and address 3

===> NOTE: 21 second delay here

[   25.862905] udev[404]: starting version 163
[   25.898443] lp: driver loaded but no devices found
[   25.931152] Adding 7812092k swap on /dev/sda5.  Priority:-1 extents:1 across:7812092k 
[   25.972740] i2c i2c-0: nForce2 SMBus adapter at 0x4140
[   25.972782] i2c i2c-1: nForce2 SMBus adapter at 0x4100
[   26.038602] lib80211: common routines for IEEE802.11 drivers
[   26.038605] lib80211_crypt: registered algorithm 'NULL'
[   26.096832] mbp_nvidia_bl: MacBookPro 5,1 detected

```

I have disabled NFS mounts and run this without network, so it think it's no network issues. The machine runs fine otherwise.

Does anyone has a clue what might cause this?

Thanks,
Mike

---

### Post by proycon on 2011-01-02
I have the same issue on a MBP5,3. The following thread describes the same problem: [http://ubuntuforums.org/showthread.php?t=1615126](http://ubuntuforums.org/showthread.php?t=1615126) , but no sign of a solution yet. Hopefully anyone knows what's causing this?

---

