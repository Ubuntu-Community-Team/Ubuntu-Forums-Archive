---
title: "PPC - anyone running usb-wireless instead of airport?"
date: 2008-12-31
forum: Apple Hardware Users
---

### Post by stream303 on 2008-12-31
Has anyone had any luck using a usb wireless stick with their ppc macs with Ubuntu, rather than the airport card?

I have a G5 iMac, and while I have been able to get both a Netgear and a Belkin usb wireless stick to get recognized, and even be able to see other networks, I can never get any dhcp offers.

Here's the background:

Both sticks are easily up and running with Debian Lenny on my AMD64.  I can use either network manager, or just do it manually from /etc/network/interfaces - they both work just great.  Obviously I had to download the ralink-firmware or zd1211 modules from the repos but they work just fine there.

In fact, the Netgear WG111v2 even works just fine with the G5 in OSX!  I downloaded the driver from the Netgear website (even though it specifically states that it is for G4's only - it works just as well on my G5).

It doesn't matter if the router is running totally open, or running wpa, or even has mac-filtering turned off.  I can run and control every aspect of the wireless sticks with either NM or wireless tools.  I can iwconfig and iwlist all day and see everthing, but nothing seems to provide me with a dhcp response - but ONLY with the Mac running Linux does this fail.

Anyone aware of any usb-stick "gotchas" for the ppc that I'm not aware of?  Is there something in openfirmware that only lets the usb wireless be receive-only?

---

### Post by stir-crazy on 2009-02-11
My wife uses my Hawking USB HWU8DD Rev. B dish adapater with great results.  This on a 300Mhz G3 iBook!

This is a great dish for any computer.

---

### Post by tygoerlitz on 2009-02-11
Hey I am looking into getting one of these things for my iBook G3 that is running ubuntu 8.10. Any suggestions?

Thanks

---

