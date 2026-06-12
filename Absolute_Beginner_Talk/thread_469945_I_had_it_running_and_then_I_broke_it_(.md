---
title: "I had it running and then I broke it :("
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by Mark1948 on 2007-06-10
I had everything running fine and learning my way about fine. Then I booted this morning and got only 640x480 resolution :( and no option to increase it.

I downloaded the ATI X1600 mobility drivers from ATI and installed them, big mistake as now I only get a flashing cursor when I reboot.

I can boot to the console and have a net connection so what command do I type to uninstall the new driver and put the old one back?

Cheers

---

### Post by taurus on 2007-06-10
You can reconfigure X again to use ati driver for your graphic card.

Boot into recovery mode and run

```
dpkg-reconfigure xserver-xorg
```

---

### Post by Jimmyfj on 2007-06-10
You don't need to install the driver downloading it and then install it manually - Use System/Administration/Restricted Drivers Manager to install the driver for your graphics card.

I've tried broking the GUI myself and I simply chose to re-install my sysytem from scratch then installing the driver as described.

I don't know how you fix a broken GUI but I'm sure someone will come in a describe the action on that.

---

### Post by Mark1948 on 2007-06-10
Hi,

When I type "dpkg-reconfigure xserver-xorg" it replies with a message saying it doesn't know my graphics card?

Cheers for the reply

---

### Post by taurus on 2007-06-10
What happens if you just use a generic driver for your graphic card like **vesa**.  See if that works.

---

