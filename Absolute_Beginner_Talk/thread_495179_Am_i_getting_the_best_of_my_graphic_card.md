---
title: "Am i getting the best of my graphic card?"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by ferpadro on 2007-07-07
I have a Nvidia GeForce 7100 GS and yesterday when i installed ubuntu,  tried enabling Desktop Effects but then i was noticed i needed to download the nvidia restricted drivers. Did that and rebooted. Compiz worked great, but when i entered the terminal and did an lspci i noticed there wasnt the word "geforce" anywhere. Does this mean i dont have my graphic card completely installed, or im just too paranoic? :P

Anyways, here is my lspci command: 

00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP61 SMU (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: nVidia Corporation Unknown device 016a (rev a1)

In the last line where it says "unknown device" shouldnt it be "geforce 7100" or something like that?

Best regards

---

### Post by Vague on 2007-07-07
I don't think it'll make any difference in terms of performance.  If it bothers you, I think ```
sudo update-pciids
``` should make it display correctly in lspci.

---

### Post by alienexplorers on 2007-07-07
to test your display you can run from terminal 
> glxgears -printfps
it will give you the relative speed of the graphics board.

---

