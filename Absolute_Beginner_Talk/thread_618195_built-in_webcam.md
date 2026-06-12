---
title: "built-in webcam"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by faysal on 2007-11-20
i'm using ubuntu 7.10 in my laptop (NEC versa L2100). but i have a problem with my web cam. i tested it with camaroma, no cam detected. anyone can give me advise about this? thanks.. :guitar:

---

### Post by Abild on 2007-11-20
Could you post the output of lspci and lsusb?

---

### Post by faysal on 2007-11-21
lspci

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
03:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

lsusb

Bus 005 Device 002: ID 0402:5602 ALi Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 147a:e020 Formosa Industrial Computing, Inc. 
Bus 004 Device 001: ID 0000:0000

---

### Post by Pevichaey5 on 2007-11-21
if i'm correct here (i think i have the same webcam) then its a bisoncam nb pro, and these do not correctly have a driver, i have seen a few projects to get this webcam working with linux, but they seem to have stalled

[_read this round up_](http://mediakey.dk/~cc/bisoncam-ali-m5603c-linux-driver-round-up/)

i have to make do with a quickcam for msn and things

Bus 005 Device 002: ID 0402:5602 ALi Corp
Bus 005 Device 003: ID 0402:5602 ALi Corp

same camera lol

---

### Post by Inxsible on 2007-11-21
you may want to try Ekiga and use the v4l2 drivers and see if that works. In Feisty, only v4l2 drivers helped in getting my internal cam to work. Unfortunately, at that time only Ekiga provided v4l2 drivers.

In gutsy, however, my cam works in kopete too, since it provides v4l2.

My camera is different than yours, so I am not sure if it will work, but it still worth a try

---

### Post by faysal on 2007-12-03
really can't make this thing work..  :( but still, i love linux.. :-D

---

### Post by bobyy on 2007-12-03
@faysal
i tried to start this camera ...but i tell you NO chance til now nobody solve this issue 
they was some projects but they are stalled.
i have this camera on my laptop for 1 1/2 years ...believe me i tried ewerithing.
i buy another camera (cheap) and it is working great out of box with ubuntu 7.10
the camera is Genius VideoCAM messenger with this chip 
> ID 0c45:602e Microdia 


---

### Post by FriedChips on 2007-12-03
try out the uvcvideo module with v4l2 that does the trick for me just google for uvcvideo and it should be the first link

---

### Post by philinux on 2007-12-03
Try kopete too.

---

### Post by bobyy on 2007-12-03
> ID 0402:5602 ALi Corp.....@friedchips you have this chipset ?  if yes... apology i am mistinformed
for this chipset  uvcvideo or v4l2 have not driver yet ..

---

### Post by FriedChips on 2007-12-03
No I do not have that chipset but I do use uvcvideo which supports many chipsets. uvcvideo is not a part of v4l2, but it uses v4l2 so after installing the module you will need to select v4l2 as your video device in ekiga. I will post back some quick instructions for you to try in a moment.

---

### Post by FriedChips on 2007-12-03
```
svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk
cd trunk
sudo -s
make
make install
modprobe uvcvideo
exit
```
then try ekiga, but make sure video device is set to v4l2.

---

### Post by bobyy on 2007-12-03
thx man
good to know ! thx for info :)

---

### Post by FriedChips on 2007-12-03
No problem, let me know if it works for you or not.

---

### Post by bobyy on 2007-12-03
with this chip no chance
> ID 0402:5602 ALi Corp.
with this is ok 
> ID 0c45:602e Microdia
thx anyway

---

### Post by FriedChips on 2007-12-03
Just doing a little reading and I have some breaking news! With
```
ID 0402:5602 ALi Corp.
```
you are screwed! Sorry man I couldn't resist :)

---

### Post by bobyy on 2007-12-03
ya man .i know that about 1 1/2 years....:)thats the reason i tell @faysal to do not spent the time useles.. =:)

---

### Post by AbtZ on 2008-05-27
If someone is still watching this thread, check this out:
[http://ubuntuforums.org/showpost.php?p=5055135&postcount=6](http://ubuntuforums.org/showpost.php?p=5055135&postcount=6)

---

