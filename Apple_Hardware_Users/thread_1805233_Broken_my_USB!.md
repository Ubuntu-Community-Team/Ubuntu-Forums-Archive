---
title: "Broken my USB?!"
date: 2011-07-15
forum: Apple Hardware Users
---

### Post by inhumangeek on 2011-07-15
*Ubuntu 11.04, iPhone 4, iOS 4.3*

Trying to get my iPhone to connect - it worked a little while back, then something got upgraded, and it no longer works. 

Background: I was trying to fix the error "Error: DBus error org.freedesktop.DBus.Error.NoReply" by re-installing libimobiledevice, usbmuxd, etc*. My PC crashed during the re-install and I ended up having to reinstall gnome as it just wouldn't load.

Anyway, now when I plug my iPhone in, *nothing* happens. No new icon, nothing mounted in /mnt/, /media, ~/.gvfs, it's nowhere as far as I can tell... is there anywhere else to look?! 

"lsusb" does see it though:

```

paul@biffyc:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 011: ID 05ac:1297 Apple, Inc. 
Bus 001 Device 010: ID 0bc2:3000 Seagate RSS LLC 
Bus 001 Device 004: ID 0971:2005 Gretag-Macbeth AG Huey
Bus 001 Device 003: ID 03f0:2f24 Hewlett-Packard LP2475w Monitor Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

Other USB devices work OK.

So my question is - how can I encourage ubuntu to mount the phone? I'm fairly new to ubuntu so please speak slowly :o The iphone and cable work just fine - used them on laptop this evening. Not bothered about tethering or syncing, I just want to copy off photos and videos. 

I'm assuming I'll need to reinstall some packages - but which ones?
Thanks very much for any advice.

*(I had tried adding the pmcenery PPA but this didn't help)

---

### Post by inhumangeek on 2011-07-16
[http://geeknizer.com/sync-iphone-linux/](http://geeknizer.com/sync-iphone-linux/)

Fixed all my problems. I wonder if it was as simple as just doing steps 3 and 4.

---

