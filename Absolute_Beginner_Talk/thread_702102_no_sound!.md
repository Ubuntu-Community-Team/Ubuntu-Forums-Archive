---
title: "no sound!"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by familyjules74123 on 2008-02-19
I dont have any sound at all coming from my ubuntu, I know my sound works in Vista as of today (dualboot) but I just logged into ubuntu and there is not sound at all

---

### Post by jaytek13 on 2008-02-19
Do you know what sound card you are using?

---

### Post by familyjules74123 on 2008-02-19
I forget, I believe it is an Intel.  How can I check?

---

### Post by familyjules74123 on 2008-02-20
here are results from lspci if it will help at all.  I know realize there is sound, but it is only when my speakers are turned all the way up (and even then it is almost too soft to hear still).  I tried to adjust the volume through volume control but its already turned up all the way on the only two volume slides i saw in there.  Any ideas would be really great!

```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
07:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

```

---

### Post by spiderbatdad on 2008-02-20
I believe there is a bug with this sound card. 

[https://bugs.launchpad.net/alsa-driver/+bug/107821](https://bugs.launchpad.net/alsa-driver/+bug/107821)
[http://www.alsa-project.org/main/index.php/ChangeLogs](http://www.alsa-project.org/main/index.php/ChangeLogs)

You may be able to fix it by installing the linux backports. Or by using the appropriate section of this guide to rebuild alsa: [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

---

### Post by familyjules74123 on 2008-02-20
Ok I got the volume working, however now I have a problem that when headphone jack is in (speakers plug into the headphone jack) use the internal speakers still play music.

---

### Post by FuturePilot on 2008-02-20
Try manually muting the Master and bring up the Headphone.

---

### Post by familyjules74123 on 2008-02-20
yeah that works, thanks futurepilot.  I wonder if there is another way besides this to take care of this problem as I can see how it might be a nuissance to some people.  Im not that picky though

---

### Post by FuturePilot on 2008-02-20
I have that same sound card in a laptop and had the same sound problem. That was the only way I've found so far to get the headphones working. Hopefully newer versions of ALSA will fix this, or even maybe PulseAudio.

---

### Post by familyjules74123 on 2008-02-20
yeah I remember seeing your name in some of those many many many forum threads and websites I read through :lolflag:

---

### Post by FuturePilot on 2008-02-20
> **familyjules74123 said:**
> yeah I remember seeing your name in some of those many many many forum threads and websites I read through :lolflag:

Hehe :lolflag:

---

