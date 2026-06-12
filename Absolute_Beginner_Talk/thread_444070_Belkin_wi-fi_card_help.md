---
title: "Belkin wi-fi card help"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by DasLemm on 2007-05-15
I'm trying to install a Belkin wi-fi pci card a F5D7010 if i'm not mistaken.
after reading other posts on the subject, i've found that the 'lspci' command could help...

```
~$ lspci
00:00.0 Host bridge: ALi Corporation M1541 (rev 04)
00:01.0 PCI bridge: ALi Corporation M1541 PCI to AGP Controller (rev 04)
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:04.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 01)
00:06.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
00:0c.0 CardBus bridge: Texas Instruments PCI1420
00:0c.1 CardBus bridge: Texas Instruments PCI1420
00:0e.0 VGA compatible controller: Trident Microsystems Cyber 9525 (rev 49)
00:0f.0 IDE interface: ALi Corporation M5229 IDE (rev c2)
00:12.0 Communication controller: Agere Systems F-1156IV WinModem (V90, 56KFlex) (rev 01)
06:00.0 Ethernet controller: ADMtek 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 11)

```
 I have installed the ndiswrapper, although i don't know which version.

so, any help is good help.
Thanks in advance!

---

### Post by jargoman on 2007-05-15
your card is not shown under lspci
from searching google I think your card uses the bcmwl5 driver found here

[http://www.xpefiles.com/viewtopic.php?t=433&](http://www.xpefiles.com/viewtopic.php?t=433&)

extract this, go into the extracted folder

$ sudo rmmod ndiswrapper
$ sudo rmmod bcm43xx (I don't think this is needed for your card but do it anyway)
$ sudo ndiswrapper -i bcmwl5.inf
$ sudo modprobe ndiswrapper

you should install network manager or knetworkmanager if you don't have it already. If you can connect then you want this to become permanent and load on boot, so

$ sudo gedit /etc/modules
then add: ndiswrapper 
$ sudo gedit /etc/modprobe.d/blacklist (again may not be needed but do it anyway won't hurt)
then add: blacklist bcm43xx

---

