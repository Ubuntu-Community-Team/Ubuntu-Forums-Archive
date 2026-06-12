---
title: "Ethernet Driver for Compaq Presario 6330CA"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by altonbr on 2008-01-12
I won't even get into my frustration with vendor-lock-in and why I'm converting my neighbour back from Ubuntu to Windows XP (*ahem* iPod touch) but I'm getting extremely frustrated with Windows' inability to install its own drivers and reliance on third-party manufacturers to supply them.

Thus, can anyone help me find the proper Ethernet driver for my neighbour's Compaq Presario 6330CA?

Here's the driver list: [http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=228&lc=en&cc=us&dlc=en&product=213857&lang=en](http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=228&lc=en&cc=us&dlc=en&product=213857&lang=en)
and here's the product specifications: [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00009597&lc=en&cc=us&dlc=en&product=213857&lang=en](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00009597&lc=en&cc=us&dlc=en&product=213857&lang=en)

I've also ran some freeware (eww) on the computer to detect the Ethernet driver. It can't, but all I can tell you is that CPU-Z has returned that the motherboard is a Compaq 0804h.

Of course, if you Google 'Compaq 0804h' you get a whole bunch of spam 'download these driverz!!!' type websites.

Any help (especially if it's "How to get an iPod Touch running in Ubuntu with no WiFi") would be much appreciated. Thank you!

(I am already aware of [https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone), but this user doesn't have WiFi...)

---

### Post by dcstar on 2008-01-12
> **altonbr said:**
> I won't even get into my frustration with vendor-lock-in and why I'm converting my neighbour back from Ubuntu to Windows XP (*ahem* iPod touch) but I'm getting extremely frustrated with Windows' inability to install its own drivers and reliance on third-party manufacturers to supply them.

Thus, can anyone help me find the proper Ethernet driver for my neighbour's Compaq Presario 6330CA?
..........

If it is new hardware then the drivers for it may not be in the kernel yet, or they may be in a kernel not available in the version of Ubuntu you are trying to run.

You can try and find out yourself if the hardware is supported in the current kernel, and then try and find a version (or compile the kernel yourself).

---

### Post by altonbr on 2008-01-13
> **dcstar said:**
> If it is new hardware then the drivers for it may not be in the kernel yet, or they may be in a kernel not available in the version of Ubuntu you are trying to run.

You can try and find out yourself if the hardware is supported in the current kernel, and then try and find a version (or compile the kernel yourself).

I'm switching FROM Ubuntu to Windows. Ubuntu runs the Ethernet driver fine. I'm only switching to Windows because of the lack of iPod Touch support in Ubuntu due to Apple's wonderful vendor lock-in.

---

