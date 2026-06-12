---
title: "Still can't get WiFi working"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by digitig on 2007-09-27
I still can't get Feisty Faun to recognise my Marvell Libertas 802/11b/g wireless card.

I've gone through the instructions at [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper), and the likely entry in the driver list is:
#Card: Marvell 88W8335 - Libertas 802.11b/g Wireless (rev 03)

    *Chipset: Marvell 88W8335
    *pciid: 11ab:1faa (rev 03)
    *Driver: [http://www.encore-usa.com/download/driver/ENLWI-G_Driver_Utility_98SE-ME-2000-XP.zip](http://www.encore-usa.com/download/driver/ENLWI-G_Driver_Utility_98SE-ME-2000-XP.zip). Used WinXP driver.
    *Other: [http://www.encore-usa.com/product_item.php?region=us&bid=2&pgid=4&pid=15](http://www.encore-usa.com/product_item.php?region=us&bid=2&pgid=4&pid=15) (product profile)
    *Other: Ndiswrapper 1.34, Recompiled kernel 2.6.18.3, without smp, with kernel debug and without 4kstacks. Debian Testing “Etch”. WPA not tested.

I don't understand most of that, but I downloaded the first of the listed drivers and installed it as described in the Ndiswrapper help. ndisgtk didn't seem to do anything at all, so I used sudo ndiswrapper -i.

When I do ndiswrapper -l I get {name of driver}  driver present but not hardware present.

I can't work out where to go next. What isn't helping is that there's no way I can get an ethernet cable to the the computer, so I have to reboot into MS-Windows to download anything or look at online documentation, then reboot back into Ubunto, which is all *very* slow :(

Can anybody tell me where to go next, before I give up completely and claim back the disk space as a Windows partition?

TIA.

---

### Post by ddrichardson on 2007-09-27
It would appear to be the wrong windows driver in use.

---

### Post by indie56 on 2007-09-27
Hello
I also have a Marvell chipset for my wifi. I followed the instructions in this document :[https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3](https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3)
I started by downloading the two files for ndiswrapper and using the CD that came with my USB wifi.
It works

---

