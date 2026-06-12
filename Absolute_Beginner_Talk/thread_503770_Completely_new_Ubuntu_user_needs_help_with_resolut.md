---
title: "Completely new Ubuntu user needs help with resolution"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by butterandguns on 2007-07-18
Okay.  So I'm brand new to Uduntu (Just installed it yesterday).  Almost everything is perfect except for the fact that my screen seems kind of stretched horizontally.  I'm guessing this is a resolution issue.  I checked the Screen Resolution Preferences but the only options there are 1024X768, 800X600, and 640X480 and the only option fro refresh rate is 61Hz.  1024X768 is closest to normal but it is still sort of stretched.  I read a few of the other posts on this and they tell to use xorg but I'm not sure what to do in xorg.  I would really really appreciate step by step detailed instructions on this.  Thank you

---

### Post by locke.dragon on 2007-07-18
we're gonna need some more info.  like what graphics card you use...

---

### Post by butterandguns on 2007-07-18
lspci says this.  hopefully this has the info you need.

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:05.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
03:05.2 Generic system peripheral [0805]: O2 Micro, Inc. Integrated MMC/SD Controller (rev 01)
03:05.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)

---

### Post by locke.dragon on 2007-07-18
hmmm.  you've got an nvidia card.  sorry.  can't really help there.  i've got an intel and i fixed it just by installing 915resolution.  :p  it's not that simple with nvidia (from what i've heard).  but don't let this simple problem deter you from ubuntu.  ubuntu's a great os and really shines once you've got it up and running.  ;)

---

### Post by butterandguns on 2007-07-18
Thanks anyway man.  I appreciate it.  And I'm def gonna be sticking with Ubuntu.

---

### Post by CautionaryX on 2007-07-18
Which drivers are you using for the nvidia card?

---

### Post by butterandguns on 2007-07-18
How would I figure out the drivers?

---

### Post by CautionaryX on 2007-07-18
```
glxinfo | grep render
```

It'll let us know if you've got 3d working and what type of card it is.

---

### Post by butterandguns on 2007-07-18
Okay
running that last command logged me out of ubuntu.
It went to a black screen with some writing and then took me to the Ubuntu login screen.

---

