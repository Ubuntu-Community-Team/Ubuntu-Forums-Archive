---
title: "LAN Driver for Biostar TF7025-M2 board?"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by yangli on 2007-09-02
I installed Ubuntu 7.04 on my machine which has a Biostar TF7025-M2 board. Everything works fine (video, sound...) except the network. The network is not working.

Do I need to download the LAN driver for Ubuntu and install it? I checked Biostar's website and there are not drivers for this board. I need help, thank you very much.

---

### Post by yangli on 2007-09-02
Any help here? Really frustrated.

---

### Post by overdrank on 2007-09-02
> **yangli said:**
> Any help here? Really frustrated.

HI could you post the out put of the command in the terminal
```
lspci
```
The terminal is located under applications, accessories, terminal.

---

### Post by yangli on 2007-09-02
The output is the following:

00:00.0 RAM memory: nVidia Corporation Unknown device 0547 (rev a2)
00:01.0 ISA bridge: nVidia Corporation Unknown device 0548 (rev a2)
00:01.1 SMBus: nVidia Corporation Unknown device 0542 (rev a2)
00:01.2 RAM memory: nVidia Corporation Unknown device 0541 (rev a2)
00:02.0 USB Controller: nVidia Corporation Unknown device 055e (rev a2)
00:02.1 USB Controller: nVidia Corporation Unknown device 055f (rev a2)
00:04.0 USB Controller: nVidia Corporation Unknown device 055e (rev a2)
00:04.1 USB Controller: nVidia Corporation Unknown device 055f (rev a2)
00:06.0 IDE interface: nVidia Corporation Unknown device 0560 (rev a1)
00:07.0 Audio device: nVidia Corporation Unknown device 055c (rev a1)
00:08.0 PCI bridge: nVidia Corporation Unknown device 0561 (rev a2)
00:09.0 IDE interface: nVidia Corporation Unknown device 0550 (rev a2)
00:0b.0 PCI bridge: nVidia Corporation Unknown device 0562 (rev a2)
00:0c.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:0d.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:0e.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:0f.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:10.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:11.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation Unknown device 053e (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)


Thanks.

---

### Post by overdrank on 2007-09-02
> **yangli said:**
> The output is the following:

00:00.0 RAM memory: nVidia Corporation Unknown device 0547 (rev a2)
00:01.0 ISA bridge: nVidia Corporation Unknown device 0548 (rev a2)
00:01.1 SMBus: nVidia Corporation Unknown device 0542 (rev a2)
00:01.2 RAM memory: nVidia Corporation Unknown device 0541 (rev a2)
00:02.0 USB Controller: nVidia Corporation Unknown device 055e (rev a2)
00:02.1 USB Controller: nVidia Corporation Unknown device 055f (rev a2)
00:04.0 USB Controller: nVidia Corporation Unknown device 055e (rev a2)
00:04.1 USB Controller: nVidia Corporation Unknown device 055f (rev a2)
00:06.0 IDE interface: nVidia Corporation Unknown device 0560 (rev a1)
00:07.0 Audio device: nVidia Corporation Unknown device 055c (rev a1)
00:08.0 PCI bridge: nVidia Corporation Unknown device 0561 (rev a2)
00:09.0 IDE interface: nVidia Corporation Unknown device 0550 (rev a2)
00:0b.0 PCI bridge: nVidia Corporation Unknown device 0562 (rev a2)
00:0c.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:0d.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:0e.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:0f.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:10.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:11.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation Unknown device 053e (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)


Thanks.

Ok if you can use the command
```
sudo update-pciids
```
this will update your ids and then run the lspci command again and post the output, thanks

---

