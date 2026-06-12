---
title: "Ubuntu 6.06.1 LTS"
date: 2007-05-23
forum: Apple Intel Users
---

### Post by liberalist on 2007-05-23
Hi everyone,

I had installed Ubuntu 7.04 on my iMac with Intel Core 2 Duo processor, but with limited success. My Airport Extreme (a/b/g/n-draft) card was not working and there were no (orange-coloured) progress bars in dialogs when (e.g.) installing updates. 

Ubuntu 6.06.1 seems more compatible with my Intel iMac. I have heard that it offers Airport Extreme compatibility 'out of the box', is this true?

Thank you very much in advance.

---

### Post by atoponce on 2007-05-23
To the best of my knowledge, Dapper Drake does not provide any support that Feisty doesn't already.  If your wireless isn't working in Feisty, chances are good that it won't work in Dapper also.  I could be wrong, though.

Feisty supports wireless pretty well, so if you could tell us what the wireless chipset in your iMac is (still Broadcom?), we can help you get it up and running, probably.

---

### Post by Greywhind on 2007-05-23
Ubuntu 6.06 (Dapper Drake) is certainly not better for Intel Macs than 7.04 (Feisty Fawn). For one thing, it's much harder to install because it doesn't automatically install GRUB to the correct location, meaning that you may have to manually configure LILO to get it to even boot up.

Also, the driver management in Feisty is much better (System->Administration->Restricted Manager), and you can get your wireless card working with a bit of effort. I did on my iMac.

So tell us more information - what wireless card do you have?

---

### Post by ronocdh on 2007-05-23
> **Greywhind said:**
> Ubuntu 6.06 (Dapper Drake) is certainly not better for Intel Macs than 7.04 (Feisty Fawn). For one thing, it's much harder to install because it doesn't automatically install GRUB to the correct location, meaning that you may have to manually configure LILO to get it to even boot up.

Also, the driver management in Feisty is much better (System->Administration->Restricted Manager), and you can get your wireless card working with a bit of effort. I did on my iMac.

So tell us more information - what wireless card do you have?
Totally agreed. With my Atheros chipset in my MacBook Pro, I don't think I'm able to use the Restricted Drivers Manager (please correct me if I'm wrong!), so I've still had to resort to using ndiswrapper or madwifi, but nonetheless, all the other things Feisty has added have been a real dream. Changing screen brightness, eject key functionality, volume and mute keys... it really makes being in Ubuntu a lot more like home.

There are tons of threads in this forum about configuring wireless, but we'll be glad to help. To find out your wireless chipset, type this in a terminal:```
sudo update-pciids
```Then:```
lspci
```Your wireless card will be near the end of the list.

---

### Post by liberalist on 2007-05-23
Information on my wireless card (taken from Apple's System Profiler; I hope that's okay):
**Wireless Card Type:**	AirPort Extreme  (0x14E4, 0x87)
**Wireless Card Locale:**	Worldwide
**Wireless Card Firmware Version:**	Broadcom BCM43xx 1.0 (4.80.79.1)
**Wireless Channel:**	11 Broadcom 

I have already tried numerous things (installing bcm43xx-fwcutter and something with ndiswrapper, see [the thread titled Airport Extreme for more details]("http://ubuntuforums.org/showthread.php?t=437205")), but none of them helped.

Please post how you got your wireless card working in your iMac again here, it might be useful for me to get things working. Thank you very much in advance.

---

