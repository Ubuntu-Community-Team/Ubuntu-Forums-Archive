---
title: "connecting to internet using a usb/ethernet converter"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by orwellus on 2007-09-23
Hello:

I have a really old computer (like 10 years old), but I install some more memory, and was able to successfully install xubuntu feisty. However, the computer is so old that it does not have a ethernet connection for my DSL router. I have a usb/ethernet network adaptor, however, and was able to hook up the computer to the router, that way. The problem is I can't get xubuntu to recognize my network connection. I have a laptop (that has regular ubuntu) and another computer hooked up to the router and both work fine. Also when my old computer still had WIndows 98, I tried the usb network adaptor on it, and it worked fine. So any help would be appreciated. I still have the cd that installs the driver for the usb/ethernet adaptor, but I'm not sure how to install that in xubuntu. The old computer I have is a Gateway Astro (all in one system). Here is a picture of the adaptor:

[IMG]http://www.geocities.com/kmlogue/ad.jpg[/IMG]

---

### Post by overdrank on 2007-09-23
Ok I just tried my usb adapter which is a Linksys USB200m but it should be the same principal. I had to reboot after attaching the device and then go to applications,system, network and configure the device and then activate it. I hope this helps and good luck! :KS

---

### Post by orwellus on 2007-09-23
Thank you for the reply. I'm still a newbie, so bear with me. How did you configure the device? I went to the network section, but I'm not sure what to do there.

---

### Post by overdrank on 2007-09-23
> **orwellus said:**
> Thank you for the reply. I'm still a newbie, so bear with me. How did you configure the device? I went to the network section, but I'm not sure what to do there.

In the network you should see a wired connection there. Click on it and like me I selected enable this connection, and in configuration I select DHCP. Now your connection may not be the same as mine.

---

### Post by orwellus on 2007-09-25
Sorry about the delay. Well I tried what you suggested, and unfortuately it did not work. I don't see a listing for a wired connection or "eth0". The only thing that is recognized is the internal dial-up modem that came pre-installed inside the computer. I think what the problem is, is that xubuntu is not recognizing the driver for the ethernet network adaptor. Does anyone know how to fix that?I do still have the cd that came with the adaptor but I'm not sure how to install the driver for xubuntu. Is there a set up wizard similar the one that ubuntu uses to set up printers?

---

### Post by overdrank on 2007-09-25
> **orwellus said:**
> Sorry about the delay. Well I tried what you suggested, and unfortuately it did not work. I don't see a listing for a wired connection or "eth0". The only thing that is recognized is the internal dial-up modem that came pre-installed inside the computer. I think what the problem is, is that xubuntu is not recognizing the driver for the ethernet network adaptor. Does anyone know how to fix that?I do still have the cd that came with the adaptor but I'm not sure how to install the driver for xubuntu. Is there a set up wizard similar the one that ubuntu uses to set up printers?

Ok one more thing try and use the command in the terminal 
```
lsusb
```
see if the device is found.

---

### Post by orwellus on 2007-09-26
Thanks for the reply. Yes, it the adaptor is listed.

---

### Post by overdrank on 2007-09-26
> **orwellus said:**
> Thanks for the reply. Yes, it the adaptor is listed.

So I am assuming you have it working now?

---

### Post by orwellus on 2007-09-26
No the internet is still not working. And the adaptor still does not show up in Network settings. But it does show up under lsusb. The adaptor is listed as 0a45: 9601: Davicom Superconductor, Inc.

---

### Post by overdrank on 2007-09-26
> **orwellus said:**
> No the internet is still not working. And the adaptor still does not show up in Network settings. But it does show up under lsusb. The adaptor is listed as 0a45: 9601: Davicom Superconductor, Inc.

Hi, I have searched and found nothing so I am just going to suggest that maybe you pick up the Linksys USB200m as I know it works. Good luck! :(

---

