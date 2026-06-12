---
title: "How My laptop fares with Ubuntu - HP dv5020"
date: 2006-04-07
forum: Absolute Beginner Talk
---

### Post by shane.reid on 2006-04-07
Used line for 6 years prior to my current job, didn't have the time to install Linux on my new corp laptop.. that one broke.. I got to pick this one, and decided to put Linux on it.

Hvaing not used Linux for a few years, I didn't use Gentoo (my former distro) and chose Ubuntu.

Breezy did not like my gfx card... so I went with Dapper flight 5

1.8ghz AMD Turion64
1gb Ram
ATI Radeon Xpress 200m
BCM4318 wifi card
Targus Bluetooth module
Bluetooth mouse
Palm Treo 650

Issues upon clean install:

1) Wifi card
Solution: get .inf file from driver cd, ndiswrapper -i inf file
rmmod bcm43xx
modprobe ndiswrapper
ifup eth0
Status: WORKING

2) Palm syncing
Solution: add /proc/bus/usb/  /proc/bus/usb/  usbfs    none        0       0
to /etc/fstab - reboot, works like a charm in evolution now
Status: WORKING

3) itunes m4a collection
**Status; NOT WORKING in rhtyhmbox (works in xmms)**

4) 1.1gb .pst file from outlook 2003
Solution: install thunderbird in windows, import mail, then import that mbox into evolution
Status: WORKING

5) Bluetooth DUN with Cingular Treo 650
**Status: NOT WORKING**

I'll try to keep this updated, since this seems to be a fairly popular HP laptop right now

And many of my issues are likely shared with others...

---

### Post by earobinson on 2006-04-07
nice simple read!

---

