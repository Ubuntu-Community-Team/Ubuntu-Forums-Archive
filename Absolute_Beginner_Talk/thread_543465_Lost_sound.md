---
title: "Lost sound"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by xt828 on 2007-09-05
I just installed Kubuntu 7.04, and after running Automatix and rebooting my computer, I've lost sound.  Before rebooting, sound was working fine, and it works fine when I boot into XP.  In Kubuntu atm I have no sound whatsoever - no log-on sound, nothing.  I have no idea how to do stuff in Kubuntu so a little hand-holding would be great.

---

### Post by Sef on 2007-09-05
What are your computer specs?

---

### Post by Oceanic on 2007-09-05
Happened to me as well.

Launch Kmixer to check whether everything is muted

There are green/red tiny buttons over each slide.

Totally worthless if you are colourblind like I am by the way.

---

### Post by bjstabio on 2007-09-05
I also have lost sound.  Installed 7.04 & 7.10 & neither have any sound.  I have another drive with 6.10 installed and sound works perfectly.  These drives are in the same box so shouldn't be a hardware problem.  I checked alsamixer and can't find anything muted.  Don't know what to do next???

---

### Post by xt828 on 2007-09-05
I opened up Kmix and nothing was muted, but the wrong soundcard is showing up.  I have a broken onboard soundcard(broken as in snapped-off jack wedged inside) and a PCI Soundblaster Audigy Value - my headphones are plugged into the latter.

---

### Post by xt828 on 2007-09-05
lspci gives me
```

xt828@mk2lin:~$ lspci
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev a2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:07.0 Multimedia audio controller: Creative Labs SB Audigy LS
01:08.0 RAID bus controller: Silicon Image, Inc. SiI 3114 [SATALink/SATARaid] Serial ATA Controller (rev 02)
01:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
01:0a.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
02:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7800 GTX] (rev a1)

```
if that's at all helpful.

---

### Post by xt828 on 2007-09-06
Okay, I ran through [this](http://ubuntuforums.org/showthread.php?t=205449) thread, and it looks like my card is being detected and has drivers loaded and so forth - but when I load up alsamixer, it seems to be for the onboard sound, not the SB.  By that I mean alsamixer displays settings for a NVidia CK804, when the card I'm after is loaded as CA0106.  How do I change which card alsamixer affects?

---

