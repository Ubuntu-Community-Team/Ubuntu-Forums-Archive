---
title: "Airport toggle on mactel"
date: 2009-05-14
forum: Apple Hardware Users
---

### Post by TessR on 2009-05-14
Hi guys. 

I'm new to Linux and installed jaunty on my mactel 1.1 recently. My question is how to turn off my airport card and turn on a USB one. My router is at one end of the house and from the other end I need the external antenna on the USB dongle to connect. The airport card is on by default and I can't find how to switch it off. Also how do I turn on the USB adapter when I connect it. And since I'm here, how do I turn off Bluetooth which is also on be default. 

Thanks

---

### Post by cyberdork33 on 2009-05-14
there is no simple way to "turn off" your airport card. You can unload the driver module that operates it though. What that module is depends on the specific card however.

A lot of usb adapters are supported. just plug it in and see if it has something available.

you can stop the bluetooth services by running:
```
sudo /etc/init.d/bluetooth stop
```

---

### Post by TessR on 2009-05-14
Thanks for the info. If I unload the driver does that power down the card? I'm concerned about 2 wifi devices being so close together when both are operating.

---

