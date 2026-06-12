---
title: "iPod and other mass storage devices aren't accessible"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by tartarian on 2007-11-08
Heya =]
I've just tried to plug my usb and ipod into my computer, but when I do nothing happens. I already have other devices plugged in, such as my wireless adapter but it just doesn't detect mass storage devices. When I try plugging them into the ports that are definatley working the problem doesn't solve itself. Bizarrley, my devices show up when I run the command lsusb, but I can't access the files and it doesn't seem to recognise them. Here's the output of my lsusb:
```

Bus 001 Device 002: ID 046d:c50a Logitech, Inc.
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 002: ID 05ac:1209 Apple Computer, Inc.
Bus 002 Device 003: ID 050d:7050 Belkin Components F5D7050 ver 1000 WiFi
Bus 002 Device 001: ID 0000:0000

```
Any ideas???
Thanks for any help!!!

I'm running kubuntu dapper btw!

---

### Post by bcrom on 2007-11-08
Try

sudo umount -a

then

sudo mount -a

That should remount all your devices.

---

### Post by tartarian on 2007-11-08
Thanks for your help!
I tried that, but it just sai!d my devices were busy and failed. Then i tried mounting everything again, but it still didn't show up!
HELP :(

---

### Post by HermanAB on 2007-11-08
You need to configure some things.  Here is something that may help, some googling will find more information:
[http://www.aeronetworks.ca/ipod-howto.html](http://www.aeronetworks.ca/ipod-howto.html)

Cheers,

Herman

---

### Post by tartarian on 2007-11-08
Heya!  I tried following that tutorial but it didn't work. The ipod just isn't showing up under either /mnt or /media, it only shows when i run lsusb but thats no use because I obviously need to access the files :(
How annoying is this?! All my music's on my kubuntu box!!! :(

---

