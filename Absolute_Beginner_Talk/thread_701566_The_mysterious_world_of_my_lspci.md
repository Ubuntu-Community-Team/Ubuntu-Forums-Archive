---
title: "The mysterious world of my lspci"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by theinnercityhippy on 2008-02-19
Hello,

i posted a different thread earlier about getting my audio and hotkeys working but realised that I may have a bigger problem which would solve the lot. In short, when I view my lspci output (see below) I get a lot of unknown devices with anything related to Nvidia (I have clicked on the enable restricted drivers tab to get this to work) and I think this is all connected to not having the right drivers for my motherboard installed.

Is this normal or has anyone any idea how I can get this issue resolved? I have a HP Pavilion DV9605ea and whilst Ubuntu seems to work OK I'm hoping I can get better performance and sound quality if I can find the correct drivers,

Thanks again lovely people

jimdog@jimdogsbrain:~$ lspci
00:00.0 RAM memory: nVidia Corporation Unknown device 0547 (rev a2)
00:01.0 ISA bridge: nVidia Corporation Unknown device 0548 (rev a2)
00:01.1 SMBus: nVidia Corporation Unknown device 0542 (rev a2)
00:01.2 RAM memory: nVidia Corporation Unknown device 0541 (rev a2)
00:01.3 Co-processor: nVidia Corporation Unknown device 0543 (rev a2)
00:02.0 USB Controller: nVidia Corporation Unknown device 055e (rev a2)
00:02.1 USB Controller: nVidia Corporation Unknown device 055f (rev a2)
00:04.0 USB Controller: nVidia Corporation Unknown device 055e (rev a2)
00:04.1 USB Controller: nVidia Corporation Unknown device 055f (rev a2)
00:06.0 IDE interface: nVidia Corporation Unknown device 0560 (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation Unknown device 0561 (rev a2)
00:09.0 IDE interface: nVidia Corporation Unknown device 0550 (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation Unknown device 054c (rev a2)
00:0c.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:0d.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation Unknown device 0531 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 02)
jimdog@jimdogsbrain:~$

---

### Post by markitect on 2008-02-19
Well it looks like you have an nforce chipset on your motherboard.  Going over to the Nvidia web site and downloading the appropriate platform Linux drivers may clean up your output, but I've never really found this to be needed to get stuff working, but I also don't have a current nforce platform.

---

### Post by theinnercityhippy on 2008-02-20
Thanks markitect. I'll head over there now and have a mooch. I'll post back any success/failure for others.

Result=failure

Ok been to the site and it seems they're adamant the chipswet is supported by the Gutsy kernel so who am I to argue :-)
 Got a good idea of what might be the problem from the following thread:

[https://answers.launchpad.net/ubuntu/+question/22924](https://answers.launchpad.net/ubuntu/+question/22924)

seems it may just be something as simple as lspci recognising the device but not knowing it's name. Ah that's linux and big corporations, always playing catch-up lol. Hopefully it will be ok once the full release of Hardy goes live. Looks like I'm doomed to have crap sound quality until then.

---

