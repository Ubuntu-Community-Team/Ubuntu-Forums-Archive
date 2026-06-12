---
title: "Modesetting Error New Install"
date: 2013-11-15
forum: Any Other OS
---

### Post by starving030 on 2013-11-15
I just installed Ylmf OS. Everything seems fine except when boot up. I get an error with some options.

> (EE) VESA: Kernel modesetting driver in use, refusing to load
(EE) No devices detected

If I choose the reconfigure option it does and tells me to restart. I choose the restart serverx(think thats the name) option and all is fine. But I have to do it every time I boot. 

I did some searching and found someone say they fixed it with editing and adding "nomodeset" in the /etc/default/grub. Most of the stuff I found I didn't understand. So I tried that and it stopped the error but then made me not able to use "Visual Effects" or adjust the Hz on my monitor.

I am new to Linux so any advice would be great. I've used up all my Linux knowledge on what I've done so far. Thanks

> 00:00.0 RAM memory: NVIDIA Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: NVIDIA Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: NVIDIA Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: NVIDIA Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB controller: NVIDIA Corporation MCP61 USB 1.1 Controller (rev a2)
00:02.1 USB controller: NVIDIA Corporation MCP61 USB 2.0 Controller (rev a2)
00:04.0 PCI bridge: NVIDIA Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: NVIDIA Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: NVIDIA Corporation MCP61 IDE (rev a2)
00:08.0 IDE interface: NVIDIA Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
02:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV515 [Radeon X1300/X1550]
02:00.1 Display controller: Advanced Micro Devices, Inc. [AMD/ATI] RV515 [Radeon X1300/X1550 Series] (Secondary)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)


---

### Post by oldos2er on 2013-11-15
Moved to Other OS/Distro Support.

---

### Post by starving030 on 2013-11-16
This seemed to work.

> possible you still have an xorg.conf trying to load drivers.

look in /etc/X11

if you've got a xorg.conf file - rename it and reboot

ref:[http://ubuntuforums.org/showthread.php?t=1497063&p=9382520#post9382520]("http://ubuntuforums.org/showthread.php?t=1497063&p=9382520#post9382520")

---

