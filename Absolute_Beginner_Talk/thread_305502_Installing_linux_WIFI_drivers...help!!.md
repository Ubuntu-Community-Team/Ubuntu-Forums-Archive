---
title: "Installing linux WIFI drivers...help!!"
date: 2006-11-23
forum: Absolute Beginner Talk
---

### Post by chlorinekid on 2006-11-23
I've messed around with various linux distros for a few years but they've
never really stayed on my machine for very long. I'm determined to make an
effort with Ubuntu though and want to keep it running on the my laptop...

The problem I have is getting the wifi working
on the laptop. I have some sort of intel wifi build into the laptop and as
far as I can see they provide linux drivers on the website which I've
downloaded. I think that if I can get these drivers installed then I should
be able to get the wifi working but I have no idea how to install them...

I've read the readme files provided but they're chirping on about things
about which I know nothing and I feel a bit out of my depth to be honest.
I've uploaded the files here --> [http://www.box.net/public/2dxx9bafpy](http://www.box.net/public/2dxx9bafpy) is anyone able to take a look
at them and tell me how best to get them installed?

---

### Post by Bachstelze on 2006-11-23
Strange, mt IPW3945 was detected by Ubuntu without needing to install the drivers from Intel... First, are you pretty sure you have an ipw2200 ? If so, try this :

```
sudo modprobe ipw2200
```

---

### Post by chlorinekid on 2006-11-23
its possible that it is the ipw3945 driver, i have that one downloaded also, i just didnt know which one was the one to use, i fugured if someone told me id try it for all the ones i have downloaded untill it worked!!

i tried the code, ipw2200 just didnt return anything and ipw3945 returned: ERROR: could not find intel pro/wireless 3945 network conection

any ideas?

---

### Post by Bachstelze on 2006-11-23
```
lspci
```

will tell you what card you have, please paste the output.

---

### Post by chlorinekid on 2006-11-23
dave@dave-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:02.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
01:02.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
01:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:05.0 Ethernet controller: Winbond Electronics Corp Unknown device 0033

---

### Post by Bachstelze on 2006-11-23
No IPW2200 here, unless I'm going blind...

---

### Post by chlorinekid on 2006-11-23
ok so its not that one...how do i find out which wireless adapter i have??

---

### Post by chlorinekid on 2006-11-23
am i right in assuming i just extract the drivers and type:

./configure
make
make install

??? just noticed this in another post...

---

### Post by burwaco on 2006-11-23
The intell 2200 is recognized by dapper and edgy, so I think you must have another card...

00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 21)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 21)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
02:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
02:04.1 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
02:04.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
02:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
02:04.4 Class 0805: Texas Instruments PCI6411, PCI6421, PCI6611, PCI6621, PCI7411, PCI7421, PCI7611, PCI7621 Secure Digital (SD) Controller
02:05.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
[B]02:06.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
[/B]

---

### Post by Duroon on 2006-11-23
If you have a windows driver disk for your wireless card you can probably get it running using ndiswrapper. 

1. Run the Synaptic package manager
2. do a search for ndiswrapper
3. check the ndisgtk package for install, it will tell you it needs several additional packages, say ok to install all of them

Once installed you will have a new option under you system/administration menu called windows wireless drivers. Run this program with your windows wireless driver disk in the cdrom drive. Choose install, navigate to the .inf file that corresponds to your installed wireless card and select it. Your card should work after that.

---

