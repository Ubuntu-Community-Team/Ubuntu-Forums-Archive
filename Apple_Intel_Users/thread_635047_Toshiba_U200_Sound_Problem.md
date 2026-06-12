---
title: "Toshiba U200 Sound Problem"
date: 2007-12-08
forum: Apple Intel Users
---

### Post by psepsas on 2007-12-08
Hi all,
        I am working on Ubuntu 7.10 release and i have sound problems. I can hear only when i plug strong headphones and extremely low.I 've done many suggestions from this forum,like:[http://ubuntuforums.org/showthread.php?t=568463&highlight=solved+sound](http://ubuntuforums.org/showthread.php?t=568463&highlight=solved+sound)
[http://ubuntuforums.org/showthread.php?t=616845&highlight=ad1981+solved](http://ubuntuforums.org/showthread.php?t=616845&highlight=ad1981+solved)
[http://ubuntuforums.org/showthread.php?t=314383&highlight=ad1981](http://ubuntuforums.org/showthread.php?t=314383&highlight=ad1981)
and many other.
Now i have installed the newest available alsa drivers
and i have added those lines to  /etc/modprobe.d/alsa-base
options snd-hda-intel model=toshiba 
options snd-hda-intel position_fix=1 model=toshiba 
options snd-hda-intel model=3stack 
This is my **_ my lspci_**
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
03:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
03:0b.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
03:0b.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
03:0b.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
03:0b.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

Thanks a lot
psepsas

---

