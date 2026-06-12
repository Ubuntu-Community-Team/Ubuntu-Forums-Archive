---
title: "Cannot boot ubuntu from live cd"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by nosh on 2007-08-03
I am trying to install feisty fawn on my brother's laptop from the live cd.  After starting on the 32 cd, everything works normally, the screen pops up and I click the run/install ubuntu and it goes through the loading bar and then the text output loading drivers and such, but gets a series of errors when loading hardware drivers for device "/class/firmware/0000:03:00.0", but the okay pops up and it continues as normal right up until the point where the screen blacks out and I expect the cursor and the login screen to appear, but instead it stays black indefinitely.  So I tried starting with the AMD 64 live boot CD and this time it freezes right after it says "* Configuring network interfacess...  [ OK ]", and the screen never blacks out, and it still gets the same device errors.

This is the computer in question:
[http://www.walmart.com/catalog/product.do?product_id=6004504](http://www.walmart.com/catalog/product.do?product_id=6004504)

Can anybody help me?  would it help if I used the alternate install CD?

---

### Post by Rocket2DMn on 2007-08-03
Yes, try the alternate install CD since it gives a text based install and doesn't require the Xserver.  The screen is probably going black when it tries to run the live session with X which might not support the video driver or monitor right out of the box.  Once the install is complete you can troublsheet the GUI by getting the correct drivers.

---

### Post by nosh on 2007-08-03
How would I go about trouble shooting the GUI and getting the correct drivers once it installs?  (I am currently downloading and/or burning the alternate install right now)

---

### Post by Rocket2DMn on 2007-08-03
Well, that depends on your video card.  I think it should probably work, maybe with low resolution which you can fix by running
```
sudo dpkg-reconfigure xserver-xorg
``` and using TAB to move around and SPACEBAR to select.  Choose your monitor's highest res and everything less when you get to that page.  Use CTRL+ALT+BACKSPACE to restart the Xserver after that, and you will be able to select higher resolutions.
If for some reason that doesn't quite work, you should try installing the restricted drivers.  Ask about that if it comes up.

---

### Post by nosh on 2007-08-03
Installation succeeded!  And it booted up with the proper resolution too, though I'm having some problems with the wireless card.  The laptop appears to have a switch for turning the card on and off, but flipping it one way or the other makes no change.  We have a home network, which I am using right now from xubuntu edgy from my own laptop,  Under network settings on the problem laptop it says roaming mode enabled.  Any help?

---

### Post by st33med on 2007-08-03
Tell us the output of this:
```
lspci
```

---

### Post by nosh on 2007-08-03
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

### Post by st33med on 2007-08-03
[Follow this HOWTO]("http://ubuntuforums.org/showthread.php?t=297092&highlight=Broadcom"). I don't know how a Dell WLAN could get on your HP Pavilion, But whatever.

---

### Post by nosh on 2007-08-03
yeah, that is weird...
I think that wraps up everything i need,
thank you very much to everyone!  It's cool how friendly and helpful opensource projects are, keep up the good work.

---

