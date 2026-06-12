---
title: "I can't get the sound to work, and i've tried alot of things."
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by Vandorin on 2008-03-29
I've tried googleing it, and looking on threads posted here, but i still cannot get the sound to work. nothing on the alsamixer is muted. does anyone know what to do?!?!?!

---

### Post by Lord Illidan on 2008-03-29
What's the make of your soundcard?

Can you open a terminal, type lspci, and copy/paste the output here, please?

---

### Post by Vandorin on 2008-03-29
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
0a:03.0 Ethernet controller: Atheros Communications, Inc. AR2413 802.11bg NIC (rev 01)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

---

### Post by Vandorin on 2008-04-03
bump

---

### Post by TeoBigusGeekus on 2008-04-03
Perhaps:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/92825]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/92825")
[https://answers.launchpad.net/ubuntu/+question/14434]("https://answers.launchpad.net/ubuntu/+question/14434")
[https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

---

### Post by code kill on 2008-04-03
I had same problem on my notebook. If you have done all updates, try this. It worked for me. Right click on the sound icon, goto preferences. Then goto the "external amplifier" and click on it to mark it. After you have chosen it, then go back to volume control, click "switches"  Then unselect "external amplifier". After this, make sure when you right click on the sound icon, and go to volume control, everything is not muted. This is what I had to do to get sound. Took me a while, when I came across, laughed to myself. Let me know if that worked.

---

### Post by code kill on 2008-04-03
I had same problem on my notebook. If you have done all updates, try this. It worked for me. Right click on the sound icon, goto preferences. Then goto the "external amplifier" and click on it to mark it. After you have chosen it, then go back to volume control, click "switches" Then unselect "external amplifier". After this, make sure when you right click on the sound icon, and go to volume control, everything is not muted. This is what I had to do to get sound. Took me a while, when I came across, laughed to myself. Let me know if that worked.

---

### Post by taavikko on 2008-04-03
Looks like you have intel integrated soundcard.
what does command **lsmod |grep snd** say, paste here!

---

