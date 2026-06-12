---
title: "WPC54G Troubles"
date: 2005-07-13
forum: Absolute Beginner Talk
---

### Post by Ebene on 2005-07-13
First off, first time Linux user and I'm loving it.

I've followed the instructions on most tutorials, but I can really only get to where I open up Synaptic Package Manager, do a search, find and install. From there on I'm lost.

Can anyone give me a good detailed instruction on how to get my WPC54G Linksys card to be compatible with my system? I have no ethernet cords so getting my laptop connected is pretty much impossible without this.

I have the Linksys driver CD and everything. Someone please help?

Thanks,
Alex  :)

---

### Post by Ebene on 2005-07-13
Bump, someone... please? I need this to be up and running by Thursday night.

Alex

---

### Post by poofyhairguy on 2005-07-13
You have two choices here.

This:

[https://wiki.ubuntu.com/HowToSetUpNdiswrapper?highlight=%28ndiswrapper%29](https://wiki.ubuntu.com/HowToSetUpNdiswrapper?highlight=%28ndiswrapper%29)

Or this:

[http://www.linuxant.com/driverloader/?PHPSESSID=2ba7ed0be70ce8ef902c9c8faea6a789](http://www.linuxant.com/driverloader/?PHPSESSID=2ba7ed0be70ce8ef902c9c8faea6a789)

EDIT:
here is more:

[http://www.ubuntuforums.org/showthread.php?t=5645&highlight=wpc54g](http://www.ubuntuforums.org/showthread.php?t=5645&highlight=wpc54g)

---

### Post by Ebene on 2005-07-13
[QUOTE=poofyhairguy]You have two choices here.

This:

[https://wiki.ubuntu.com/HowToSetUpNdiswrapper?highlight=%28ndiswrapper%29](https://wiki.ubuntu.com/HowToSetUpNdiswrapper?highlight=%28ndiswrapper%29)

Or this:

[http://www.linuxant.com/driverloader/?PHPSESSID=2ba7ed0be70ce8ef902c9c8faea6a789](http://www.linuxant.com/driverloader/?PHPSESSID=2ba7ed0be70ce8ef902c9c8faea6a789)

EDIT:
here is more:

[http://www.ubuntuforums.org/showthread.php?t=5645&highlight=wpc54g](http://www.ubuntuforums.org/showthread.php?t=5645&highlight=wpc54g)[/QUOTE]
 [https://wiki.ubuntu.com/HowToSetUpNdiswrapper?highlight=%28ndiswrapper%29](https://wiki.ubuntu.com/HowToSetUpNdiswrapper?highlight=%28ndiswrapper%29)

Everything is good until I get to "sudo modprobe ndiswrapper" I get this error:

FATAL: Error inserting ndiswrapper (lib/modules/2.6.10-6-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted

---

### Post by Ebene on 2005-07-13
It's obviously detecting the card because the network icon in the panel changes if I insert or remove the card. However, the power light isn't coming on while the card is in.

---

### Post by poofyhairguy on 2005-07-13
[QUOTE=Ebene]It's obviously detecting the card because the network icon in the panel changes if I insert or remove the card. However, the power light isn't coming on while the card is in.[/QUOTE]

Is it a version 2?

---

### Post by Ebene on 2005-07-13
yes

---

### Post by Nequeo on 2005-07-13
I've seen this problem once before - it occured because there was a mismatch between the version of NDIS wrapper I was using and the kernel modules (my theory, anyway).

You might want to try removing ndiswrapper completely and building version 1.2 of NDIS wrapper from the source. That's what it took to get my wireless card (a Linksys PCI) working. 

Follow the instructions here:
[https://wiki.ubuntu.com/SetupNdiswrapperHowto?highlight=%28ndiswrapper%29](https://wiki.ubuntu.com/SetupNdiswrapperHowto?highlight=%28ndiswrapper%29)

the only change you might want to make is downloading the 1.2 source from here:
[http://optusnet.dl.sourceforge.net/sourceforge/synergy2/synergy-1.2.2.tar.gz](http://optusnet.dl.sourceforge.net/sourceforge/synergy2/synergy-1.2.2.tar.gz)
instead of version 1.1.

---

