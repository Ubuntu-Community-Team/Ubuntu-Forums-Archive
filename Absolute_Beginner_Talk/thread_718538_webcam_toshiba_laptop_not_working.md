---
title: "webcam toshiba laptop not working"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by DGGARCIA on 2008-03-08
Hi,

I'm trying to record myself with my integrated camera but I think is not installed. I tried as well to use it with amsn and is not working either. The thing is I only need to record a video.I don't really mind the camera en amsn...

Does anyone know how to get the integrated webcam to work and also what kind of program to use if i want to take pictures/video with it?

Thanks in advance

---

### Post by tdrusk on 2008-03-08
> **DGGARCIA said:**
> Hi,

I'm trying to record myself with my integrated camera but I think is not installed. I tried as well to use it with amsn and is not working either. The thing is I only need to record a video.I don't really mind the camera en amsn...

Does anyone know how to get the integrated webcam to work and also what kind of program to use if i want to take pictures/video with it?

Thanks in advance

Please open a terminal, type
```
lspci
```
and copy that and paste it here.

---

### Post by DGGARCIA on 2008-03-08
Hi man, Thats what appear:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
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
01:00.0 VGA compatible controller: nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300] (rev a1)
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
06:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
06:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
06:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
06:04.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

---

### Post by tdrusk on 2008-03-08
Hmm that didn't help. 

Can you post your laptop model and maybe a link to it?

---

### Post by DGGARCIA on 2008-03-08
Its a toshiba satellite A200 series

[http://eu.computers.toshiba-europe.com/cgi-bin/ToshibaCSG/jsp/seriesHomepage.do?service=EU&SERIES_ID=127420](http://eu.computers.toshiba-europe.com/cgi-bin/ToshibaCSG/jsp/seriesHomepage.do?service=EU&SERIES_ID=127420)

probably this one: [http://eu.computers.toshiba-europe.com/cgi-bin/ToshibaCSG/jsp/productPage.do?service=EU&PRODUCT_ID=144958](http://eu.computers.toshiba-europe.com/cgi-bin/ToshibaCSG/jsp/productPage.do?service=EU&PRODUCT_ID=144958)

but i'm not sure of the exact model.

is that of any help??

---

### Post by LuisGMarine on 2008-03-08
If its integrated in the screen run this command:

```
lsusb
```

Post the output of that command, if you have this line :
```
[COLOR="Red"]
Bus 006 Device 003: ID 04f2:b008 Chicony Electronics Co., Ltd [/COLOR]
```

then you are stuck, there seems to be no support for it yet on Linux, sorry.  I've tried every program, right now , I'm missing one and trying to find it that is suppose to make it work, but so far nothing successful.

---

### Post by DGGARCIA on 2008-03-08
Yes, that whats appear:

Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 04f2:b008 Chicony Electronics Co., Ltd 
Bus 003 Device 001: ID 0000:0000 

Thanks man for your time. I&#314;l keep trying and searching.

If you find something else, let me know.

thanks again.

---

