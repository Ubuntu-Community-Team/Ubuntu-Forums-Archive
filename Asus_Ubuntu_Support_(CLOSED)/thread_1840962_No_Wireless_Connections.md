---
title: "No Wireless Connections"
date: 2011-09-08
forum: Asus Ubuntu Support (CLOSED)
---

### Post by TarioTheBard on 2011-09-08
I've been wrestling with my refurbished eeePC 901 linux edition for the past 6 months and I've finally decided to ask for help.

My most lasting problem has been the wireless which first stopped showing itself in the panel (fixed, problem with puredyne and network manager) then it stopped acknowledging the presence of wireless networks in general and finally gave up on the Internet all together, refusing to acknowledge the network cable that I had to plug in to replace the wireless.

Weirdly the lattermost problem has disappeared as mysteriously as it came leaving me with wired internet again. However the wireless still doesn't work.

I've replaced the network card with a different one (from a Dell) and then again with a replacement Atheros (original card type). Neither card made any difference so I put the original back in.

I've run the original Asus Linux release, Puredyne and EasyPeasy on it with the same effect. Wired internet but no wireless.

It seems similar to this post but my lspci output is different

 [http://ubuntuforums.org/archive/index.php/t-1129208.html](http://ubuntuforums.org/archive/index.php/t-1129208.html) 



lspci:
```


00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
04:00.0 Ethernet controller: Atheros Communications Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller (rev b0)

```Compared to the other thread I'm missing a "Network controller".

Any idea where it went?

---

