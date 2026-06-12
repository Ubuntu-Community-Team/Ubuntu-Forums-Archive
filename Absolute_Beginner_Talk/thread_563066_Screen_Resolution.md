---
title: "Screen Resolution"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by Riyonuk on 2007-09-29
After finally being able to boot in Ubuntu (Had to re-insert the wireless mouse/keyboard usb device), I saw that the resolution is so not right. So how do I go about fixing this? I saw in other posts that they wanted people to type "lspci", so I did too.

```
riyonuk@ubuntu:~$ lspci
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
00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
04:07.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
04:08.0 Communication controller: Conexant HSF 56k Data/Fax Modem
```

I have a Dell E521. Am I supposed to update the monitor drivers? If so, I have no idea how :/

---

### Post by Nikitas350 on 2007-09-29
Go to system--->administration--->restricted drivers manager. You can install easily install the drivers from there. If this fails you can change the resolution if you edit the xorg.conf....

---

### Post by Riyonuk on 2007-09-29
Ok I did what you said. It automatically started downloading something, and asked for me to restart. When I did, the ubuntu logo was still offset, but the login screen looked great! Out of curoisity, I checked in the Screen Resolution settings, and it said I was using 1280x1024. Now I know that in Vista, it told me the native resolution was 1440x900, why isn't it listed?

---

### Post by Nikitas350 on 2007-09-30
Open the terminal and type "gedit /etc/X11/xorg.conf" post here what is appears and i will tell you what you should change in order to change the resolution to 1440x900. (The new version of ubuntu will autodetect the resolution... if all fails you can wait 17 days :) ) Good luck

---

