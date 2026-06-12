---
title: "Wireless Problems"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by Kiioro on 2007-12-16
I just finished installing ubuntu and there were no problems... until I tried getting online. I enter the information, as it seems to detect the wireless hardware, but as I try to configure it, the whole thing freezes (currently writing from my laptop).

The hardware, just in case it's needed:

COMPUTER
Motherboard - "ASUS" P5B 
Graphics - "PowerColor" HD2600 
Wireless PCI Adapter - "Airlink 101" 802.11G
Processor - "Intel" Core 2 Quad

WIRELESS MODEM
"Motorola" SBG900 Wireless Surfboard Gateway

---

### Post by wankel on 2007-12-16
Hi Koiiro,

What program do you use for connecting to the wireless network? On my wifes laptop, the "Wireless Assistant" freezes the system sometimes upon connecting. 

Using "KWifimanager" (it's Kubuntu) or command line there is no problem.

Then again, on a desktop system I have problems not related to the way of connecting: there I have a PCI card with a Broadcom chipset and restricted drivers. They will hang the system no matter what. If your problem is something like that, 

I unfortunately can not help you (that system is connected by wire as well, so I did not look into it yet). I would start with finding out which chip set is being used on your PCI card, for example by opening a terminal and using "lspci -vv" to get information about your PCI devices. It is quite a lot of information you will see, but there will also be information about the chip set on your wireless card.

---

### Post by jfank on 2007-12-16
> **Kiioro said:**
> I just finished installing ubuntu and there were no problems... until I tried getting online. I enter the information, as it seems to detect the wireless hardware, but as I try to configure it, the whole thing freezes (currently writing from my laptop).

The hardware, just in case it's needed:

COMPUTER
Motherboard - "ASUS" P5B 
Graphics - "PowerColor" HD2600 
Wireless PCI Adapter - "Airlink 101" 802.11G
Processor - "Intel" Core 2 Quad

WIRELESS MODEM
"Motorola" SBG900 Wireless Surfboard Gateway

I wish I had a answer to help you out, but here is another topic on this forum that has a lot of replies dealing with wireless problems.  Check it out, you might be able to find something here.

[**[COLOR="Blue"]If you are having wireless problem in Gutsy[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=594857")

---

### Post by Kiioro on 2007-12-16
I see... where can I find the Kwifimanager? It seems to come only in the whole KDE package and I can't find a link to download it separately...

---

### Post by Kiioro on 2007-12-16
Ah, also, JFank, thanks, but there wasn't anything there that could help me... my wireless (after doing the lshw -C network thing):

Realtek Semiconductor Co., Ltd.
RTL-8185 IEEE 802.11a/b/g 

But, after I do the iwlist scan says:

No scan results

---

