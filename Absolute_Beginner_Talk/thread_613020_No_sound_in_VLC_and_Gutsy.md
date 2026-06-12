---
title: "No sound in VLC and Gutsy"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by petri on 2007-11-14
I had sound in VLC with the beta Gutsys but it disappeared with the final Gutsy. I have searched the forums but didn't found something that would have helped me. My motherboard is Asus M2NPV-VM and **lspci** in terminal says:

```
 ...lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51PV [GeForce 6150] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
04:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
04:08.0 Ethernet controller: Atheros Communications, Inc. AR2413 802.11bg NIC (rev 01)
04:09.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
04:09.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
```

---

### Post by TidusBlade on 2007-11-14
Not sure, but [this](http://ubuntuforums.org/showthread.php?t=588708) could be it.

---

### Post by Inxsible on 2007-11-14
you need to change the Alsa to Linux OSS in the audio sections of VLC.

startup VLC >>Settings>>Preferences>>Audio>>Output modules. 

Then click the advanced options at the bottom and then in the drop down change the output module from Alsa to Linux OSS. It seems that the alsa for vlc is broke :(

---

### Post by petri on 2007-11-14
Thanks TidusBlade and Inxsible for your posts.

But... they didn't help.

I can hear the sound in Totem but the video is jerky if it runs at all. In Koffeine both is fine (if it runs att all) untill about 40 minutes has passed and then the sound goes off but video is still fine.

In VLC there is no sound but video does work every time.

---

### Post by petri on 2007-11-20
My Gutsy installation was an upgrade from beta Gutsy. I have now done a fresh installation and everything works: [http://ubuntuforums.org/showthread.php?p=3807155#post3807155](http://ubuntuforums.org/showthread.php?p=3807155#post3807155)  msg # 17

---

### Post by lepezhr on 2008-02-07
I had the same problem, go to synaptic and install vlc alsa outup and esound, both, and then it's works
Sorry my bad English. From Argentina Hector:KS

---

