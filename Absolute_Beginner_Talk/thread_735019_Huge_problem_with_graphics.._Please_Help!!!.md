---
title: "Huge problem with graphics.. Please Help!!!"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by remali on 2008-03-25
I have a compaq presario 2540 EA. 

CPU: Pentium IV 2,66Ghz
RAM: 512MB
GPU: ATI Mobility Radeon (IGP 330M/340M/350M, auto detect)

I installed Ubuntu 7.10.
The problems are
1) I only can have resolution 800x600, otherwise it shakes.
2) Though on Windows XP I could play Warcraft III (with high graphics) and GTA etc, now in games like supertux, neverball, wormux, xmoto it is very slow and not playable. 
3) Even simple videos (.avi) are shown awful with pixels..
4) With window XP the boot time was about 30 second and now it takes at least 3:40 minutes.
5) And generally the system seems to be slower than on Windows

I searched, read and did a lot of things but nothing did work..(*,)](*,)
i need advise please. i don't wonna change to XP again :-({|=:-({|=]

---

### Post by kpkeerthi on 2008-03-25
Try these...
[https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by LowSky on 2008-03-25
first you need to grapihcs drivers, uninstall any of the ones you mght have loaded, then google for a program called Envy, install then run it to install your grphics drivers

---

### Post by philinux on 2008-03-25
Open a terminal and use

[FONT="Courier New"]lspci[/FONT]

Post the result.

---

### Post by remali on 2008-03-25
thanks for the quick replies :) :)

> **kpkeerthi said:**
> Try these...
[https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)

I have tried most of the things in that article, unfortunately with no good result

> **kpkeerthi said:**
> Try these...
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
> **LowSky said:**
> first you need to grapihcs drivers, uninstall any of the ones you mght have loaded, then google for a program called Envy, install then run it to install your grphics drivers

I downloaded Envy , unintalled the drivers and when I tried to intsall them, an error occured and this is the log:
[I]
python pulse.py ati
root@galileo:/usr/share/envy# python pulse.py ati
Envy - Version 0.9.10
Ubuntu Gutsy 32bit
ENVY ERROR: Envy does not recognise your card as compatible with any version of the driver.this might happen because either your card is not supported by the driver or Envy's hardwaredetection failed. You can try the manual installation at your risk.[/I]

Should I try manual intallation?? Is there anything I should be aware of???

> **philinux said:**
> Open a terminal and use

[FONT="Courier New"]lspci[/FONT]

Post the result.

the result is:


00:00.0 Host bridge: ATI Technologies Inc RS200/RS200M AGP Bridge [IGP 340M] (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M]
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
00:0b.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:0b.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:0b.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)
00:0c.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M

---

### Post by remali on 2008-03-25
In the manual installation of Envy I have to choose the version of ATI drivers I wish to install..Which of these 3 should I choose??

1) 8.3
2) 8.40.4
3) 8.28.8

---

### Post by remali on 2008-03-27
Ok I managed to make the games to play and to boot faster following [this]("http://ubuntuforums.org/showthread.php?t=579568&highlight=very+slow+boot+with+gusty"), but the main problem remains... ](*,) ](*,)
I only can use 800x600 resolution oherwise the screen shakes. I took a screenshot to upload but in the picture my desktop seems normal (no shaking). 
I suspect it might be the refreshing rate but I only get one choice --> 60Hz.

Can anyone please help me???

---

