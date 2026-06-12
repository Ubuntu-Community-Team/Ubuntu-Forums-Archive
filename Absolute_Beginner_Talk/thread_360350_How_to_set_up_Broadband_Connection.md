---
title: "How to set up Broadband Connection?"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by CoreTortex on 2007-02-13
Hi all, I have Ubuntu 6.10 and have BT Total Broadband with the 1055 wireless adapter.
My question is, how do I go about setting up the connection?

I don't see an internet connection wizard of any kind and haven't found any drivers for the wireless adapter (although it is shown in device manager). 

Thanks for any help

---

### Post by bigken on 2007-02-13
take a look at system administration networking make sure the device is enabled and add your essid and network password (wep) you could also right click on the task bar and add the network monitor :)

---

### Post by tyres on 2007-02-15
Hi,

The BT1055 adapter is not very easy to get working with Ubuntu. It is possible (I did it a few days ago!), but you need to be fairly comfortable with Linux to do it. Basically you need the driver files from your BT1055 installation disk, or your Windows system (if you have one). The files you need are bcmrndis.inf, rndismpk.sys and usb8023k.sys.

You need to make sure you've got 'ndiswrapper' installed, which runs Windows drivers under Linux.

Then look at the ndiswrapper supported adapters list at 
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#B](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#B)

Search for the entry with 'Gladier' at the end. This guy has posted how to get an adapter with the Broadcom 4320 chipset working with Ubuntu. The BT1055 has the Broadcom 4320 chipset inside it. Follow his instructions, then load the installed driver with ndiswrapper (the ndiswrapper page at [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)
explains how to do that).

If you can follow that, it should work for you!

Cheers,

Colin

---

