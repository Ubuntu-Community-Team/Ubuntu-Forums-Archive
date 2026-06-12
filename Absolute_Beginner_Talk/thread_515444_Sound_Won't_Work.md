---
title: "Sound Won't Work"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by Amarasu on 2007-08-02
Sorry if I am asking to much, but I started Ubuntu a week ago and have been trying to fix the sound the entire time. 

I have Intel 82801g (ICH7) sound card and Ubuntu seems to be able to detect it, but it won't work at all.

I have tried looking at other posts, but I usually run into a problem and don't know how to start.

I'm running Feisty Fawn and it doesn't work, but when running the Edgy Eft live CD, it works.

Why is the sound dropped from Edgy to Feisty?

Here is the lspci:

> 00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
04:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
06:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
06:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
06:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
06:04.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller


I'd be glad to add more information, but I'm not sure what to put. Thanks in advance to everyone.

---

### Post by Amarasu on 2007-08-02
bump?

---

### Post by hamburglar6 on 2007-08-02
type the following into a terminal window
```
alsamixer
```
and unmute anything that is muted.  also you may want to google correct alsamixer settings for your card.  i had the same problem with an old audigy card and eventually the answer was to mute 'audigy analog' and turn 'center' up for instance.

---

### Post by wolfen69 on 2007-08-02
try this:[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_make_sound_works_with_Intel_Integrated_Sound_Cards](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_make_sound_works_with_Intel_Integrated_Sound_Cards)

---

### Post by Amarasu on 2007-08-02
Really noobish question, but when it says flavor, what exact words should i put in.

---

### Post by Amarasu on 2007-08-02
what am i supposed to replace 3stack with? I'm not really sure what it means by flavor.

---

### Post by Amarasu on 2007-08-02
THANK YOU THANK YOU THANK YOU!!!! IM SO HAPPY NOW!!!!! I FINALLY HAVE SOUND!!!!!!

All I did was install Alsa using the guide from this website: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

When I booted, there was this loud white noise. I solved this by muting the micophones, and now i have sound!

THANK YOU!!!!!!!

:KS:KS:KS:KS

---

