---
title: "really new to this"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by vikki on 2008-01-13
can you please help me i dont know how to put wirlesss on the laptop can you help me with it step i have hard times doin it alone

---

### Post by EXCiD3 on 2008-01-13
What make/model wireless card do you have?

---

### Post by edm1 on 2008-01-13
If you dont know the make/model then open a terminal 'Applications>Accessories>Terminal' and type 'lspci' then post the output on here.

---

### Post by vikki on 2008-01-13
i dont use the cards it has a swich that connects anyway....is that a bad thing.

---

### Post by EXCiD3 on 2008-01-13
No thats fine, just post the output of "lspci" like edm1 said. We can help you from there. You probably just have a wireless card builtin to the motherboard, not an physically separate card.

---

### Post by vikki on 2008-01-13
ly@ly-desktop:~$ ispci

like that???

---

### Post by vikki on 2008-01-13
wait hol on i need to get on laptop

---

### Post by mmb1 on 2008-01-13
> **vikki said:**
> ly@ly-desktop:~$ ispci

like that???


Yes, except it's "lspci" instead of "ispci".   :)

---

### Post by vikki on 2008-01-13
linh@linh:~$ Ispci

ok

---

### Post by EXCiD3 on 2008-01-13
Its a lowercase L not an I. "lspci" means "List PCI".

---

### Post by vikki on 2008-01-13
oh ok ..sry 


linh@linh:~$ lspci

---

### Post by EXCiD3 on 2008-01-13
Yep thats correct ;)

---

### Post by vikki on 2008-01-13
yay.:)...so ok whats next

---

### Post by EXCiD3 on 2008-01-13
Can you post the text that it displays when using that command? We need this to determine what wireless card you have. ;)

---

### Post by vikki on 2008-01-13
so i have to copy all of this right?


linh@linh:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
04:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
06:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
06:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
06:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
06:04.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
linh@linh:~$

---

### Post by EXCiD3 on 2008-01-13
>  04:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)That is your wireless card. ;) And assuming you are using Gutsy here is a link on how to install it: [http://quilombo.wordpress.com/2008/01/09/atheros-ar5006eg-in-ubuntu-710-gutsy-gibbon/](http://quilombo.wordpress.com/2008/01/09/atheros-ar5006eg-in-ubuntu-710-gutsy-gibbon/)

And a step by step through this guide for you:

Open Terminal again and type ```
sudo gedit /etc/modprobe.d/blacklist
```Add "blacklist ath_pci" to the file
Save and exit Gedit
Enable the extra repositories by going to System->Administration->Software sources and make sure Multiverse, Universe , Main, and Restricted are checked like in this image: [IMG]http://buranen.info/wp-content/uploads/2007/10/screenshot-software-sources.png[/IMG]
In terminal type ```
sudo apt-get update
```
In terminal type ```
sudo apt-get install ndiswrapper ndisgtk
```Download this file to your desktop: [http://www.atheros.cz/download.php?atheros=AR5006EG&system=1](http://www.atheros.cz/download.php?atheros=AR5006EG&system=1)
Extract that file you just download
In terminal execute this command ```
cd ~/Desktop
```In terminal execute this command ```
sudo ndiswrapper-i net5416.inf
```In terminal execute this command ```
sudo ndiswrapper -ma && sudo ndiswrapper -mi
```Reboot

Everything should be working afterwards! :) Hope it works! Good luck!

---

### Post by vikki on 2008-01-13
thank you :) .....but im having trouble where to go on that part it like in spanish

---

### Post by vikki on 2008-01-13
ohh TY!!!!!xD ur so cool xD:):)

---

### Post by EXCiD3 on 2008-01-13
Just follow my instructions, they are the exact same, just simplified for ya! ;)

---

### Post by EXCiD3 on 2008-01-13
Any luck?

---

