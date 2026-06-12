---
title: "[SOLVED] Please Help Me Setup Wireless Acer Aspire 3680"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by tdrusk on 2007-08-08
I just bought this laptop, put Ubuntu on it, and noticed that wireless is not working. Here's my lspci:
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
03:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

```

Any guides that I can follow to get this to work. The sticker on the front says 
> 802.11b/g wireless LAN

I really need this to work. I can't take Vista!

EDIT: I just updated my pci ids and it says this is what my card is:
> 03:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)


---

### Post by overdrank on 2007-08-08
Hi you can run the command in the terminal 
```
sudo update-pciids

```
This will update the pci ids and then you will know which Atheros  you are using. Good luck and please post back if you get it working! :popcorn:

---

### Post by tdrusk on 2007-08-08
> **overdrank said:**
> Hi you can run the command in the terminal 
```
sudo update-pciids

```
This will update the pci ids and then you will know which Atheros  you are using. Good luck and please post back if you get it working! :popcorn:

Thanks. It came out with this:
```
03:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)

```

---

### Post by solar george on 2007-08-08
You could try ndiswrapper if you can get the windows drivers from somewhere.

---

### Post by overdrank on 2007-08-08
> **fuzzyhair said:**
> Thanks. It came out with this:
```
03:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)

```

Yea and vista recognize it as AR5007EG . Like I said before some have used madwifi and some have used ndiswrapper so good luck! 
[http://ubuntuforums.org/search.php?searchid=25091361](http://ubuntuforums.org/search.php?searchid=25091361)

---

### Post by tdrusk on 2007-08-08
*does a happy dance*
I followed the directions here
[http://ubuntuforums.org/showthread.php?t=512828&highlight=acer+aspire+3680](http://ubuntuforums.org/showthread.php?t=512828&highlight=acer+aspire+3680)
and it works amazingly.

---

### Post by overdrank on 2007-08-08
> **fuzzyhair said:**
> *does a happy dance*
I followed the directions here
[http://ubuntuforums.org/showthread.php?t=512828&highlight=acer+aspire+3680](http://ubuntuforums.org/showthread.php?t=512828&highlight=acer+aspire+3680)
and it works amazingly.

No way Dude, Great I will be trying it to   congrats. :KS

Sweet it works, wooohoooo its alive!!!!!!!!!

---

