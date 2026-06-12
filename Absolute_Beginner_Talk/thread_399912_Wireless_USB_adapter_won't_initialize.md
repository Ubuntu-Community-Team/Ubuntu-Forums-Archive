---
title: "Wireless USB adapter won't initialize"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by medley on 2007-04-02
Hi all

Have been enjoying Ubuntu over the last couple of months, so much so that I've now installed in on 3 systems in my house. The most recent is a lower end 1Ghz Celeron with an Intel 810 motherboard. I've installed Kubuntu Edgy, and everything works just dandy except the wireless adapter, which is a Linksys WUSB54GSv2.  It isn't being recognized by my network configuration, and it's not initializing, as far as I can tell, because the power light is not coming on.

I've installed ndiswrapper 1.8, and installed equivalent Belkin drivers per the ndiswrapper wiki. When I do 'ndiswrapper -l' I get

'bcmrndis               driver installed, hardware present'

The device is showing up correctly if I 'lsusb'. I also get an error message that says 'ndiswrapper failed to initialize' if I grep dmsg for ndiswrapper.

I've tried all of the tips I've come across, including leaving the device unplugged until after bootup, depmod, modprobe ndiswrapper, etc.

If I do 'iwconfig' I get no wireless extensions for lo, eth0, or sit0.

Any ideas?

---

### Post by medley on 2007-04-03
> **medley said:**
> Hi all

Have been enjoying Ubuntu over the last couple of months, so much so that I've now installed in on 3 systems in my house. The most recent is a lower end 1Ghz Celeron with an Intel 810 motherboard. I've installed Kubuntu Edgy, and everything works just dandy except the wireless adapter, which is a Linksys WUSB54GSv2.  It isn't being recognized by my network configuration, and it's not initializing, as far as I can tell, because the power light is not coming on.

I've installed ndiswrapper 1.8, and installed equivalent Belkin drivers per the ndiswrapper wiki. When I do 'ndiswrapper -l' I get

'bcmrndis               driver installed, hardware present'

The device is showing up correctly if I 'lsusb'. I also get an error message that says 'ndiswrapper failed to initialize' if I grep dmsg for ndiswrapper.

I've tried all of the tips I've come across, including leaving the device unplugged until after bootup, depmod, modprobe ndiswrapper, etc.

If I do 'iwconfig' I get no wireless extensions for lo, eth0, or sit0.

Any ideas?

Hmmm...the silence is deafening.

---

### Post by medley on 2007-04-04
> **medley said:**
> Hmmm...the silence is deafening.

Wow, 62 views and counting, and no other replies than me bumping my message?

---

