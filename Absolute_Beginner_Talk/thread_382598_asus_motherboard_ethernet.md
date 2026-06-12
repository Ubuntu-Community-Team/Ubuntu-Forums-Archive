---
title: "asus motherboard ethernet"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by vladinho on 2007-03-12
Hello everyone.

I'm quite new to linux and ubuntu+beryl.


My problem is the following: I have an ASUS M2NPV-MX motherboard with NVIDIA GeForce 6150 GPU chipset.

I have an NVIDIA nForce 430 MCP ethernet .. but it seems i can't get it to work. Can't find the apropriate driver. When i thought i had found one.... guess what...doesn't work.

It says that i have no precompiled kernel and when i hit enter so that he would compile one on his own... it coudn't... an error occured saying that i don't have the libc something....


can anyone PLEASE help me get through this? I had no problems at installing everything else...
but since i can't get online...i can't even update or download new stuff....


Thanks

---

### Post by astrolabio on 2007-03-12
post your /etc/network/interfaces file

and run 
sudo lspci 
and post the output too

---

### Post by vladinho on 2007-03-12
ok...i'll do that in a couple of mins... I'm on Win XP now...

---

### Post by vladinho on 2007-03-12
Here's the interface file (zipped) and the lspci paste:

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
03:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
03:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]

---

### Post by Milesowl on 2007-03-13
Hello,

I am very interested in this post. I have the same problem with the same board. The instructions for Linux drivers in the MB cd  are not very helpfull.

The ethernet won't work. And the video drivers are not ok either (few resolution options etc...)

---

### Post by Krikke_wl on 2007-07-30
Well I got the same board, network works fine, but somehow I got a lot of kernel dumps and I'm trying to figur out why, seems to me now that it could be network related... Any ideas someone??

Thanks!!

---

