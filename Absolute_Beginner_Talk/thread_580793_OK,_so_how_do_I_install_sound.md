---
title: "OK, so how do I install sound?"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by Tom Stanley on 2007-10-19
Hi everyone,

I'm completely new to Ubuntu, and need to get 5.1 sound in Ubuntu 7.10 x64. The drivers are available ([(Click)]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=23&PFid=23&Level=4&Conn=3&DownTypeID=3&GetDown=false#AC") , however I don't have a clue which version to use, and how to install it. I know I need to use Sudo, but how do I do this?

Thanks a lot for your time and patience!

Tom :)

---

### Post by montres on 2007-10-19
Hi there!
Try these steps:

Open up a terminal at: Applications menu -> Accessories -> Terminal

Type this command:
```
sudo modprobe snd-intel8x0
```

Enter your password when prompted

In the terminal, type this command:
```
alsamixer
```

Set sound volume to desired levels

Try playing an MP3

Tell me if this works!

---

### Post by Tom Stanley on 2007-10-19
Hi,

Nope, that didn't work. I think I need to install the drivers somehow?

---

### Post by FuturePilot on 2007-10-19
What's the output of ```
lspci
```

---

### Post by sleepwalker on 2007-10-19
I am having the same problem!

I am getting sound off and on though. The weird thing is, I receive sound only when my laptop is connected to an Ethernet port.

Any more hints on the ALSA mixer?
Does this problem relate to anything with digital/analog sound?

My lspci:
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
00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)
05:09.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
05:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:09.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
05:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
05:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

---

### Post by sleepwalker on 2007-10-19
Allrighty. I just upgraded to 7.10, sound was installed, and my wireless is working! (Where it  NEVER has before.) I just lost all of my Ubuntu Studio Themes,,,

---

