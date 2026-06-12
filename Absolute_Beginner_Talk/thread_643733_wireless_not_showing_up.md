---
title: "wireless not showing up"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by Vic! on 2007-12-18
helpplease :( ........ im having trouble getting a laptop's wireless to work with the new 7.10 update...if anyone can help me id greatly appreciate it.

heres some info.. my network settings dont even show a wifi connection / device thing i have a toshiba satellite....and 

lspci output

mondoe@Mondoe-laptop:~$ lspci
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


once again thank you everyone and happy holidays!!!

v

---

### Post by unknown user on 2007-12-18
Not too sure if this will help or not, but to get my wireless working I had to reset the Bios default settings.  Mine was a little different as it was showing up in the list, but when I clicked on the Network icon at the top of the screen, there was no wireless networks detected.  This was strange as I know there is always around 5 near me that always show up.
I then read a post saying that another guy had this issues (HP) and he had to go into the Bios settings on boot up and then reset the default back to original.  
It worked great for me, may be a quick thing to do to rule this one out before you try all the code that I am sure you will be bombarded with.
Good luck.:)

---

### Post by Vic! on 2007-12-18
yea mine is not even showing up i think i might have to do something else to get it to work... some people were telling me to use ndiswrapper but im not too sure how to ...if any1 can give me a hand id appreciate it :) thanx!

---

### Post by coolbrook on 2007-12-18
> **Vic! said:**
> 

lspci output

mondoe@Mondoe-laptop:~$ lspci

04:00.0 Ethernet controller: Atheros Communications, Inc. **AR5006EG** 802.11 b/g Wireless PCI Express Adapter (rev 01)


[http://madwifi.org/](http://madwifi.org/)
[http://madwifi.org/wiki/Compatibility/Atheros#AtherosAR5006EG](http://madwifi.org/wiki/Compatibility/Atheros#AtherosAR5006EG)

---

### Post by unknown user on 2007-12-18
Vic, no problem but if you are never told you never know and can not make your own decisions.
I also would like to know how to use ndiswrapper as I have heard a bit about it.:guitar:

---

### Post by Vic! on 2007-12-18
if you go [here]("http://ubuntuforums.org/showthread.php?p=3972704#post3972704") its a post i made on a network area of the forums it has lots of links that help with ndiswrapper im trying to use it right now...:) thanks alot though! any help is appreciated.

---

### Post by Vic! on 2007-12-18
thanks coolbrook if the ndiswrapper doesnt work in a few hours im definitly checking out madwifi i have it downloaded already i just havent tried to use it 


thanks again!

---

### Post by Vic! on 2007-12-20
OHHH i got it working ... sorta its not exactly pretty but im connected to wifi right now and its working  ... [heres]("http://ubuntuforums.org/showthread.php?t=645010") the details hope this works for anyone that can use it

---

