---
title: "Driver Issues"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by nsimeone2000 on 2008-02-18
Ok, I have Ubuntu Feisty Fawn loaded, I have been playing around with it and some of these tutorials are very well written, this one is specific to my Laptop and has been a huge help.
[http://ubuntuforums.org/showthread.php?t=512059](http://ubuntuforums.org/showthread.php?t=512059)

But here are some of my issues, I have downloaded the NVIDIA drivers for my laptop (which is an HP Pavillion 9000 series, 9208 specifically) so I have this .run file on my desktop, and I can't quite figure out what to do with it, NVIDIA's instructions make absolutely no sense whatsoever.

They tell me to do this: After you have downloaded the file NVIDIA-Linux-x86_64-169.09-pkg#.run, change to the directory containing the downloaded file, and as the root user run the executable:

    # cd yourdirectory
    # sh NVIDIA-Linux-x86_64-169.09-pkg#.run

So I went into the terminal, and attempted to run it, with the following commands.
sudo -s
 sh NVIDIA-Linux-x86_64-169.09-pkg#.run
(I have the file on the desktop, and when I do a cd desktop it tells me it cannot be found)

And the final issues I am having is my wireless card, I followed the instructions here:
[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

It seemed like install with the ndiswrapper and everything went through just fine, but the computer will not detect the wireless device.

I am a complete Noob, but have been tinkering now for a couple of days.  Any assistance would be greatly appreciated.

---

### Post by jan quark on 2008-02-18
first run in terminal

```
lspci
```

and post the output to detect the exact model type of your network device

then you can use the application[ envy ]("http://albertomilone.com/nvidia_scripts1.html")to install the nvidia drivers automatically

---

### Post by kesman on 2008-02-18
for changing directories, and accessing/running files, learn to use TAB-key to auto-complete file- and directory names for you. cd desktop won't do anythng, but cd Desktop does, since it's a capital D, not d. Linux is case-sensitive.

---

### Post by nsimeone2000 on 2008-02-18
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
03:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
07:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

---

### Post by nsimeone2000 on 2008-02-18
Sorry I typed it in the thread wrong, but in the terminal I was typing at case sensitive.....

---

### Post by jan quark on 2008-02-18
try this tutorial to enable the broadcom card

[http://laiconic.quotaless.com/tutorial1.html](http://laiconic.quotaless.com/tutorial1.html)

---

### Post by nsimeone2000 on 2008-02-18
I am not running a dual OS, I boycotted Windows, but if you look at the 2nd link I posted you would see where I was able to get that file already, but to no avail Ubuntu isn't registering it, unless there is something else I am supposed to do.  Like a network connections module in Ubuntu?

---

### Post by nsimeone2000 on 2008-02-18
Ok, I figured out Envy will fix the video problems, that is a neat little tool.......If we can fix this wireless issue then I am finally free.......

---

