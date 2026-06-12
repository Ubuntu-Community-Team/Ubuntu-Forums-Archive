---
title: "Ubuntu for Asus Transformer AiO p1801"
date: 2014-02-11
forum: Asus Ubuntu Support (CLOSED)
---

### Post by LogicalDash on 2014-02-11
This device is in fact two computers, a desktop and a tablet, wherein the latter docks to the former and functions as a display device, a touchpad, and secondary storage. It is impossible to buy the desktop without the tablet, though I believe the tablet is sold absent the desktop.

It comes with Windows 8, which I dual-booted for a while until a series of bad decisions, beginning with installing a custom kernel with no backup, left me with the partitions still in place, but a mysterious inability to boot into the Windows one, nor even detect it with update-grub or boot-repair. I don't honestly care that much anymore, I'm just trying to make Ubuntu work better on it now.

Ubuntu runs well enough on the desktop. The touchscreen doesn't really work--it's detected, but mysteriously disconnects with error -71 shortly thereafter. Then it keeps reconnecting and disconnecting and generally jamming up /dev/input and the system log, so I've blacklisted hid-multitouch for the time being. It's a "USBest_Technology_SiS_HID_Touch_Controller" and its USBID is 0457:0817 for whatever this means to anyone.

The use of the tablet as a storage device is problematic. It uses MTP and seems not to support the usual USB Mass Storage Device protocol. In Raring I was able to access it via KDE's support for network storage (though it is really quite local) but in Saucy, I've had to resort to adb and go-mtpfs, both as root, which is inconvenient.

The tablet itself runs Android and seems a good candidate for an Ubuntu Touch port, being that the other Transformers already have theirs--though I'm uncertain how much this tablet really resembles them.

---

### Post by alexandreperr on 2014-06-07
HI,

I have the exact same issue. I created a dual boot Win8.1 / Linux Mint 16 and it works well on Mint exept for the touch screen. Suprisingly I saw it working once or twice after coming back from hibernation, or when I was requesting a shutdown...
Have you find a way to solve that problem?

Thanks


Alex

---

