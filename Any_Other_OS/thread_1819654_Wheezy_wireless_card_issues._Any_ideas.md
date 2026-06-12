---
title: "Wheezy wireless card issues. Any ideas?"
date: 2011-08-06
forum: Any Other OS
---

### Post by teh5abiking on 2011-08-06
I recently migrated to Wheezy because some of the software I needed was hideously outdated in Squeeze, and the backports didn't supply the updated software I was looking for.

I have a Sony VAIO laptop, but it's one of the older models and doesn't come with WiFi, so for the past couple of years, I was using a Linksys WUSB54GC v3 wireless card, which I believe is part of the rt2870 chipset. 

I've followed [this tutorial on the Debian wiki]("http://wiki.debian.org/rt2800usb") to make my wireless card work like it did in Squeeze. However, after I've loaded the rt2800usb module, I typed in ```
iwconfig
``` to see if my device had a port, but I didn't see it. To be sure, I entered ```
ifconfig wlan0 up
``` in the terminal, but it said there was no such interface. 

Can anyone please tell me what's going on? 

Sent from my HTC Vision using Tapatalk

---

### Post by NightwishFan on 2011-08-08
What is the output of this command:
```
apt-cache policy firmware-ralink
```

---

