---
title: "Wireless card that &quot;just works&quot;"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by Kayma on 2006-08-21
I was wondering if anyone could recommend a wireless card for a laptop that "just works" in Ubuntu. I had a Linksys card that worked after messing with drivers, however it did not appear in Network Manager, show me signal strength in the corner and wouldn't show me available wireless networks.

---

### Post by Jagot on 2006-08-21
I'm afraid that I don't have any experience with one, but you may want to have a look through this from the wiki:

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by Saphira on 2006-08-21
It wouldn't hurt to look here either.

[http://doc.gwos.org/index.php/Main_Page](http://doc.gwos.org/index.php/Main_Page)

---

### Post by Kayma on 2006-08-21
Thank you both. These should help immensely.

---

### Post by gn2 on 2006-08-21
D-link DWL-650+ 22mbps with ACX100 Texas Instruments chipset works for me.

---

### Post by zigx on 2006-08-21
i have two dlinks that are working without prob since day 1...

also i have no idea if this is just in my mind but i think on windows the signal/connection was lost a LOT more often than when i use Ubuntu.

---

### Post by Jeff250 on 2006-08-21
If you're talking about mini-PCI, an (Intel) ipw2200 is hands down the safest and most compatible solution, especially with WPA 1&2.

---

### Post by neko18 on 2006-08-21
Wireless worked right from the start with a friend's laptop, it was an Intel Pro Wireless 2200, just like Jeff250 said.

---

### Post by LeslieL on 2006-08-21
My laptop came with an Intel PRO/Wireless 2200BG. Ubuntu (and any other Linux distro I've tried) recognized it immediately.

---

### Post by saxofoner on 2006-08-21
My friend has a BELKIN Laptop card, recognized instantly.

---

### Post by crispy_420 on 2006-08-21
I have a Netgear WG511T and it was instantly working in Ubuntu, just a little setup was done (WEP, Network Manager, etc.).

Look for something that works with network manager. Avoid Marvell chipset for native linux support. Also avoid RaLink (rt2500) if you want network manager to ever work.

So to some it up, you want to see what chipset is used before you purchase.

Good: Intel Atheros

OK: RaLink

Bad: Marvell

Just from my experience which is not too extensive.

Check here for network manager compatibility:

[http://live.gnome.org/NetworkManagerHardware](http://live.gnome.org/NetworkManagerHardware)

---

### Post by philbridges on 2006-08-23
I've used the NetGear WG511 PCMCIA card and it just 'plugged & played' incl. WPA if you also downlaod Metwork Manager from ADD/REMOVE programs

---

### Post by GordonWright on 2006-08-23
Despite some comments elsewhere the NetGear WG511T worked straight off for me (and mine is the version with "made in China" sticker).  On initial install of (ed)Ubuntu it seemed to have issues but as soon as the machine rebooted all was working.

---

### Post by benfindlay on 2006-08-23
In my experience, any wireless card that uses a PRISM (or PRISM II?) chipset will work quite well. These chipsets are very common, especially in pcmcia wireless cards for laptops. I have used them in the past with SuSE 10, but admittedly, ndiswrapper (a program that makes windows wireless drivers function under linux) was running in the background. Also you will most likely have some real issues if you want to use WPA encryption over WEP (which I would assume most people do). All in all you're much better off just running a cable to your router/switch!

---

