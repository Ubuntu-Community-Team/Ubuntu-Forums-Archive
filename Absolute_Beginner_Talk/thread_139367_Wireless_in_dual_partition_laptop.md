---
title: "Wireless in dual partition laptop"
date: 2006-03-03
forum: Absolute Beginner Talk
---

### Post by shickidyshade on 2006-03-03
ok i am using a dual boot windows and ubuntu breezy laptop that is a dell d610 and i am trying to find a way to get my wirelss to work while i am home if i do use wirelss i still need the wireless to work for both systems and not just one

thanks

shade

---

### Post by shickidyshade on 2006-03-03
This is what i get out of the terminal

~$ lspci
0000:00:00.0 Host bridge: Intel Corp. Mobile Memory Controller Hub (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. Mobile Memory Controller Hub PCI Express Po rt (rev 03)
0000:00:1c.0 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Exp ress Port 1 (rev 03)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB  UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB  UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB  UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB  UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB 2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d3)
0000:00:1e.2 Multimedia audio controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH 6 Family) AC'97 Audio Controller (rev 03)
0000:00:1e.3 Modem: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
0000:00:1f.2 IDE interface: Intel Corp. 82801FBM (ICH6M) SATA Controller (rev 03 )
0000:00:1f.3 SMBus: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Contro ller (rev 03)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 546 0
0000:02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit  Ethernet PCI Express (rev 01)
0000:03:01.0 CardBus bridge: Texas Instruments: Unknown device 8036
0000:03:01.5 Communication controller: Texas Instruments: Unknown device 8038
0000:03:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 0 3)

---

### Post by C J Pro on 2006-03-03
[https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper)

Ndiswrapper may be the solution you are looking for.  I personally haven't messed around with ndiswrapper much.  But it should do what you are looking for.

---

### Post by ariek on 2006-03-03
Hi shickidyshade,

Indeed, use the howto of the Ubuntu wiki. However, make shure to not use the latest driver for your 1450 WLAN, but the one from July last year. The file name you want is R102320.EXE, and the link where to find it is: [here]("http://support.euro.dell.com/support/downloads/download.aspx?c=nl&l=nl&s=pad&releaseid=R102320&SystemID=LAT_PNT_PM_D610&os=WW1&osl=EN&deviceid=6483&devlib=0&typecnt=1&vercnt=9&formatcnt=1&fileid=132284") 
After installing ndiswrapper-utils, and installing your driver, use iwconfig to configure your wlan settings.

Good luck,

Arie

---

