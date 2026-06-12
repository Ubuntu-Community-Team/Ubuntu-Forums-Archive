---
title: "Is there any way to get a usb mouse to work after boot up?"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by Roasted on 2007-12-13
If I boot up with my usb mouse plugged in, it works.
If I plug in the usb mouse after boot up, it doesn't work.

Is there any way to activate it if I plug it into a running system?

---

### Post by ^rooker on 2007-12-13
I use a USB mouse myself on my notebook and it's working regardless of when it was plugged in - so I assume that it's something related to your mouse/computer. 

If I'm not mistaken, USB mice and keyboards should use a default HID (human interface device) driver that's loaded automatically when hotplugging... 

Could you please provide information about which mouse (model?) you're using?

---

### Post by Roasted on 2007-12-13
Logitech M-UAG120.

In Fedora when I was running it on this very laptop, it would recognize it automatically. In Ubuntu, it appears that if I unplug it and replug it in after a full load of the OS, it needs to be rebooted to work again.

---

### Post by ^rooker on 2007-12-15
Do you have any USB mouse/keyboard settings in your BIOS?
I remember that I've seen BIOSes that could try to "cloak" USB input devices as regular ones. Worth trying to locate/change such an option...

Furthermore:
Does your mouse show up as USB device when you unplug/reconnect it?
- run "lsusb" with your mouse working and then again with it being unplugged/reconnected and see if it at least registers itself again.

---

### Post by Roasted on 2007-12-15
How would the bios make a difference? It auto-runs again in Vista if I plug it back in. But Linux is another story. 

I recall seeing it on my lsusb output. But I'll check it again later to verify it.

---

