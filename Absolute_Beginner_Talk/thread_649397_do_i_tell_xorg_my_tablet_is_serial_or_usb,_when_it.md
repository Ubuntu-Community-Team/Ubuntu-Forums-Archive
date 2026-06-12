---
title: "do i tell xorg my tablet is serial or usb, when it's a serial with a usb adaptor?"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by ijason on 2007-12-24
before i get into editing my xorg to run my old wacom tablet, i need to know whether to treat it like a usb device, or a serial? since it's a serial tablet running through a usb converter? uuuuuh???

---

### Post by Rocket2DMn on 2007-12-24
Before you touch that xorg.conf, make a backup
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
If you break xorg, replace the broken one with the backup
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

Your question is a little confusing, but you should tell it whichever is actually on the tablet.    Sounds like you want serial.

---

### Post by ijason on 2007-12-25
well, it's a serial tablet. but since i'm trying to run it on my laptop which has no serial ports, i'll be connecting it via a serial/usb adaptor. so, in the xorg, do i treat the device like a usb, or a serial?

---

### Post by forestpixie on 2007-12-25
I would tell it it's a usb - as that's what it is actually going to be connecting to. 

If it doesn't like it, try serial, but I'd be inclined to think it'll get really confused if you tell it you're connecting with a serial and you haven't got one.

Make a note of the cp backup to xorg command just in case you get dumped to the cli

---

### Post by jordank on 2007-12-25
I would say usb.  The whole point of an adapter is to change the format from serial to usb.  When it actually reaches the computer, it's in usb format.

---

