---
title: "Joli OS WiFi problems"
date: 2013-01-15
forum: Any Other OS
---

### Post by TheNate on 2013-01-15
I'm running a live usb of JoliOS, and liking it so far, but as with every other linux I've tried, I can't get my wifi working. Heres my **lscpi**:

```
jolicloud@jolicloud:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev ff)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev ff)
04:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
04:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
04:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
You have new mail in /home/jolicloud/
jolicloud@jolicloud:~$ 

```

Thanks in advance:)

---

### Post by ugm6hr on 2013-01-17
I'm not sure which version of Ubuntu JoliOS is based on.
However, you should definitely be able to get wifi to work. I have the identical wifi card, and it has worked for me since 8.04.

I currently use 12.04 (Elementary OS DE) on my Dell Mini.

Try:
Plug computer into ethernet port for wired internet
Enter following in Terminal
```
sudo apt-get remove bcmwl-kernel-source 
sudo apt-get install b43-fwcutter
sudo apt-get install firmware-b43-installer
```

Then reboot

If that doesn't work - look at the wifi help link below and provide more information. The commands may be slightly different for older versions of Ubuntu.

---

