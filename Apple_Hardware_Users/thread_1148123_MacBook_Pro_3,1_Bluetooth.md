---
title: "MacBook Pro 3,1 Bluetooth"
date: 2009-05-04
forum: Apple Hardware Users
---

### Post by lambengolmor on 2009-05-04
Hi, I wanted to use my MacBook Pro 3,1 with a bluetooth-connected GPS device (Holux GPSlim 236) for [OpenStreetMap]("http://www.openstreetmap.org")ing. So I discovered my built-in bluetooth doesn't work.
-I tryied adding a new device but in the list nothing appeared (Gps was in pairing mode)
-so I set the bluetooth option to "show only when adaptator is present" and the icon just disappeared from the taskbar
-this is my lsubs:
```
Bus 002 Device 002: ID 05ac:8502 Apple, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 003: ID 05ac:021b Apple, Inc. Internal Keyboard/Trackpad
Bus 007 Device 002: ID 05ac:8242 Apple, Inc. 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 05ac:1000 Apple, Inc. Bluetooth HCI MacBookPro (HID mode)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

Any ideas? Thanks a lot

---

### Post by cyberdork33 on 2009-05-04
Notice the Bluetooth adapter is in HID mode. See this posting for info:
[http://idebian.wordpress.com/2008/07/06/manage-hid-bluetooth-devices-in-linux/](http://idebian.wordpress.com/2008/07/06/manage-hid-bluetooth-devices-in-linux/)

---

### Post by lambengolmor on 2009-05-05
I tried to follow the tutorial you suggested me (for the whom I thank you, I learned quite a thing about BT :) ) but I have a problem I assume derives since is written for debian and not for ubuntu:

when I try ```
sudo hciconfig hci0 reset
``` I get a message about the device non-existent. So I tried some other devices: ```
$ sudo hciconfig hci1 reset
Can't get device info: No such device
$ sudo hciconfig hci2 reset
Can't get device info: No such device
$ sudo hciconfig hci3 reset
Can't get device info: No such device
$ sudo hciconfig hci4 reset
Can't get device info: No such device
$ sudo hciconfig hci5 reset
Can't get device info: No such device
$ sudo hciconfig hci6 reset
Can't get device info: No such device
$ sudo hciconfig hci7 reset
Can't get device info: No such device
$ sudo hciconfig hci8 reset
Can't get device info: No such device
$ sudo hciconfig hci9 reset
Can't get device info: No such device
$ sudo hciconfig hci10 reset
Can't get device info: No such device
$ sudo hciconfig hci0 reset
Can't get device info: No such device

```

The device is listed in lsusb as shown above, can anyone help me figure out how Ubuntu calls it?

---

