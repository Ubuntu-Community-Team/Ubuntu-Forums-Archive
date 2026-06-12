---
title: "Remove USB devices"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by freesitebuilder on 2007-02-25
We have two PCs using the internet with a cable modem, which we share using USB - that is, we can't both be online at once (which is no problem).

In Windows, before swapping the cable, we right-click the USB devices icon in the system tray, and use "remove device".

Is there an equivalent in Ubuntu, or do I need to shut down before removing the cable? The other PC only runs Windows XP Home.

I know ethernet would be a better option, but we can't switch at the moment.

TIA

---

### Post by moore.bryan on 2007-02-25
[I]with windows xp, you can just pull the cable, you don't have to "remove device;" with windows 2000, you do.  gnome asks you to "eject" the media... you can do that with a command at prompt in terminal:
```
sudo eject /dev/xxx
```
where "xxx" is the location of the device.  you can also set-up a shortcut on your desktop to get this done for you...
[/I]

---

### Post by almasry on 2007-02-25
or just right click the partition  and click (Eject) ..

---

### Post by moore.bryan on 2007-02-25
*good point, almasry... i don't use gnome/kde, so...*

---

### Post by freesitebuilder on 2007-02-26
I used lsusb to check the device location, and got
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 004 Device 004: ID 0bb2:6098 Ambit Microsystems Corp. USB Cable Modem
Bus 004 Device 003: ID 041e:4010 Creative Technology, Ltd
Bus 004 Device 002: ID 05e3:0606 Genesys Logic, Inc.
Bus 004 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

from which I thought that 004 was the device - but it doesn't like that.

---

### Post by moore.bryan on 2007-02-26
*if it's your only usb device, it's probably "/dev/sda1"*

---

### Post by jdong on 2007-02-26
Guys, this is a cable modem, not a storage device.

In most cases with these devices, it's safe just to yank them out, and Linux will take recovery actions. At most you should bring down the interface (if the modem is eth0, then do **sudo ifconfig eth0 down**) then yank it out.

---

