---
title: "how do i use my wirless card on ubuntu"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by gavinvasquez on 2006-12-28
hi i have a aspire 1690 how do i use wirless on ubuntu tnx 
specs 
Intel Pentium M Processor 740 (Processor speed 1.73GHz, 2MB L2 cache, 533MHz FSB) 
Intel 915PM Express Chipset Integrated Intel Pro/Wireless 2200BG   
256MB DDR-RAM (Max 2GB)   
80GB HDD, Weight 2.95kg.   
DVD-Dual Double Layer Drive 
4-in-1 card reader   
56K Fax/Modem, 10/100/1000Mbps LAN   
15.4" WXGA Acer CrystalBrite TFT LCD(1280x800 pixel) 
S-Video Out   
ATI Mobility Radeon X600 64MB   
Li-Ion Battery (3.5 hrs. battery life)   
IEEE 1394 port 
Infrared port 
Integrated Bluetooth 
Acer SignalUp wireless technology support   
Microsoft Windows XP Home

---

### Post by jimrz on 2006-12-28
> **gavinvasquez said:**
> hi i have a aspire 1690 how do i use wirless on ubuntu tnx 
specs 
Intel Pentium M Processor 740 (Processor speed 1.73GHz, 2MB L2 cache, 533MHz FSB) 
Intel 915PM Express Chipset Integrated Intel Pro/Wireless 2200BG   
256MB DDR-RAM (Max 2GB)   
80GB HDD, Weight 2.95kg.   
DVD-Dual Double Layer Drive 
4-in-1 card reader   
56K Fax/Modem, 10/100/1000Mbps LAN   
15.4" WXGA Acer CrystalBrite TFT LCD(1280x800 pixel) 
S-Video Out   
ATI Mobility Radeon X600 64MB   
Li-Ion Battery (3.5 hrs. battery life)   
IEEE 1394 port 
Infrared port 
Integrated Bluetooth 
Acer SignalUp wireless technology support   
Microsoft Windows XP Home

Welcome

ran a search for "2200bg" (searching these forums is a great way to find answers to most questions about ubuntu) and found these links:

[https://help.ubuntu.com/community/Wi...CardsSupported](https://help.ubuntu.com/community/Wi...CardsSupported)
[http://www.ubuntuforums.org/showthread.php?t=263136](http://www.ubuntuforums.org/showthread.php?t=263136)

seems that your card is supported, but takes a bit of extra work to get functioning properly

---

### Post by teejay17 on 2006-12-28
First of all, you have to inform us what version of Ubuntu you're using. If you're using 6.10 "Edgy Eft," you might want to try installing the [FONT="Courier New"]restricted-modules[/FONT] that can be found in the Synaptec Package Manager. This is something you should try before venturing down the Ndiswrapper path, as it's much easier, and often works. 
Once you install this package, reboot the system.

---

### Post by gavinvasquez on 2006-12-29
yes i am using 6.10

---

### Post by teejay17 on 2006-12-29
How's the [FONT="Courier New"]restricted-modules [/FONT]working out for you? Were you able to get your wireless card working with that?

---

### Post by teejay17 on 2007-01-07
Dude, you gotta keep us posted as to your progress.

---

