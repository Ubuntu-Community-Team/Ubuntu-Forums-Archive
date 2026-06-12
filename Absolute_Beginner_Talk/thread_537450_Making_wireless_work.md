---
title: "Making wireless work"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by coolkid5 on 2007-08-28
Hello,

I have just installed ubuntu 7.04 64bit on the computer i just built, and i need help getting the internet working.  I'm using an ASUS m2n32-sli deluxe wireless edition.  Is there a way that i can use the built in wifi to connect to the internet.  If so, could someone please tell me how to do so. If not, what must i get to make this work.  I've read something about "ndiswrapper" but i don't know what it is or if it will help me. Please help me to make this work.

And please make it so that someone like me can understand what to do.  I haven't used ubuntu before.

Thanks in advance.

---

### Post by coolkid5 on 2007-08-28
Parts-
M2N32-SLI Deluxe Wireless edition
AMD Athlon X2 5200+
nVidia Geforce 7600 GT
If someone could even point me to a thread or site that could help me that would be great.

---

### Post by reset3x on 2007-08-29
> **coolkid5 said:**
> Parts-
M2N32-SLI Deluxe Wireless edition
AMD Athlon X2 5200+
nVidia Geforce 7600 GT
If someone could even point me to a thread or site that could help me that would be great.

try ```
sudo lshw
``` to see what your chipset is then we'll go from there....

---

### Post by coolkid5 on 2007-08-29
I typed "sudo lshw" and the terminal returned a really long thing that didn't fit.  I scrolled to the top but it didn't go all the way back.  
Could you be more specific.  What chipset did you want me to give you.

---

### Post by anewguy on 2007-08-29
Then let's try "lspci" and have you post that output back here.:)

---

### Post by coolkid5 on 2007-08-29
Here is what sudo lspci said.
```
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2) 
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2) 
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2) 
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2) 
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2) 
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2) 
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2) 
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2) 
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) 
00:08.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1) 
00:09.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2) 
00:09.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2) 
00:09.2 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2) 
00:0a.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1) 
00:0a.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2) 
00:0c.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1) 
00:0d.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2) 
00:0d.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2) 
00:0d.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2) 
00:0e.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2) 
00:0e.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2) 
00:10.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2) 
00:11.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2) 
00:16.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2) 
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport
Technology Configuration 
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map 
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller 
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control 
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1) 
02:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller 
(PHY/Link) 
03:00.0 Mass storage controller: Silicon Image, Inc. SiI 3132 Serial ATA Raid II Controller (rev 01) 

```
Also I'd like to point out that the wireless antenna came with the motherboard and it does not plug into a usb or pci.  Asus calls it WiFi-AP Solo and it plugs into a special antenna port on the back of the computer.

---

### Post by anewguy on 2007-08-30
Thanks for posting that output.  I don't think I'll be able to help because my limited experience with this is with using Windows drivers and ndiswrapper.  I don't see your wireless card listed in the output, so I assume that would be why reset3x asked for the output of the lshw command, as it would show the hardware devices on your system.  If you can't scroll the terminal window up far enough to get to the beginning where you entered the "sudo lshw" so that you therefore can't copy and paste the entire thing here,  look for something about a wireless ethernet adaptor, copy it, and paste it back here.  Without a maker/chipset for the wireless adaptor, we may not be able to get you there.  I'm going to do some more searching and I'll post back later.:)

---

### Post by kevdog on 2007-08-30
Try posting the following:
lshw -C network

---

### Post by anewguy on 2007-08-30
Okay, I went to the ASUS  USA site and downloaded the Windows driver for your device.  I am attaching the 2 files as an archive.  Download the archives and extract to your desktop, then do the following:

- go to synaptic package manager and search for ndiswrapper
- click the box in front of ndiswrapper itself and select install
- do the same for ndiswrapper-utilities-xxxxxxxxxx  <- probably some extra stuff where the x's are
- click apply and let it install ndiswrapper and the utilities
- close out of synaptic package manager

If you have not installed network-manager and network-manager-gnome, repeat the above searching for network-manager and check network-manager and network-manager-gnome then apply to install and then close out


- open a terminal window and type the following:

sudo ndiswrapper -i ~/Desktop/Netrtuw.inf
sudo ndiswrapper -m
sudo depmod -a
sudo modprobe ndiswrapper
 
- close the terminal window

Hopefully you now can click on the network icon on the top bar and see the available wireless networks and connect to yours.

Please post back if you have any more problems or if you get it to work.:)

---

### Post by kevdog on 2007-08-30
Install ndiswraper from svn or compile and install from source code.  Please do not install the ndiswrapper version from repository.  Its very old and can cause conflicts for some people.  If you need instructions, then ask.  Please post lshw -C network so we can diagnose the problem before making any moves.

---

### Post by anewguy on 2007-08-30
> **kevdog said:**
> Install ndiswraper from svn or compile and install from source code.  Please do not install the ndiswrapper version from repository.  Its very old and can cause conflicts for some people.  If you need instructions, then ask.  Please post lshw -C network so we can diagnose the problem before making any moves.

Hi kevdog!  You've helped me out in the past!  I'm at the end of my very limited knowledge, so I'm going to leave him to you - thanks buddy!:)

---

### Post by kevdog on 2007-08-30
Im retiring soon, so you are going to become the expert!!! I think this thread might be dead, not getting any response from the originator.

---

