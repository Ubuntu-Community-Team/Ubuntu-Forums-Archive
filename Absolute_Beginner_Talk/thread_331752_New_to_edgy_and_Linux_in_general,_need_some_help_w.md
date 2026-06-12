---
title: "New to edgy and Linux in general, need some help with my wireless card (etc etc...)"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by nextse7en on 2007-01-05
Ack with a side of ack, Vista DRM issues have ported me away from MS for good, ubuntu is my replacement of choice, as it seemes mature (unlike say freespire, which I think could probably really be somewhere 2 or 3 versions from now) and Fedora Core, which doesn't seem as friendly.

After finding out that I could use WINE to run photoshop, flash, and Maya, It didn't take much to convince me to switch to Linux.  That being said, my HP doesn't seem to be supporting my decision much, and after spending 2 days just to get it to install (I finally found that the "noapic" kernel startup argument kept the system from hanging), I'm struggling with the WIFI, and with NVIDIA drivers.

I've gone thru the broadcom howto for 4311 cards, to no avail, all I get is another network manager that loads next to the first one. Could someone help me on this front? 

My lspci output is as follows.

pwilson@pwilson-tank:~$ lspci
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
03:00.0 Network controller: Broadcom Corporation Unknown device 4311 (rev 01)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
07:05.1 Class 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
pwilson@pwilson-tank:~$ 
  

Whats up with the broadcom corporation unk. device? is this my problem, that instead of getting bcom corp wireless card 4311 I'm getting unk device?

And help on this front would be greatly apprieciated, also, could someone tell me how to shut down X and drop to the command line? I need to to this evidentally to install the nvidia driver.



Thanks!
Patrick

---

### Post by imonlyhuman on 2007-01-05
Run ```
sudo update-pciids
``` in a terminal.

That should get it updated/remove unkown device.

Took it from here. [http://www.ubuntuforums.org/showthread.php?t=315497&highlight=sd+reader](http://www.ubuntuforums.org/showthread.php?t=315497&highlight=sd+reader)

Theres a link there for getting your Rioch reader working (on the 4th page i believe):D

Oh, and I dont know about shutting down X, but if you press Crtl+Alt and F1 to F6, you will get a command line, you just need to login. Crtl+Alt+F7 will bring you back to X.

On installing the driver, ill do some research, or maybe someone else can help :rolleyes: . I have never really installed a driver before, Ubuntu just worked for me.  :-D

---

### Post by nextse7en on 2007-01-05
LOL, now its calling it a.

Dell Wireless 1390 WLAN

But still Broadcom

---

### Post by Famicommie on 2007-01-05
> **imonlyhuman said:**
> Run ```
sudo update-pciids
``` in a terminal.

That should get it updated/remove unkown device.

Took it from here. [http://www.ubuntuforums.org/showthread.php?t=315497&highlight=sd+reader](http://www.ubuntuforums.org/showthread.php?t=315497&highlight=sd+reader)

Theres a link there for getting your Rioch reader working (on the 4th page i believe):D

Oh, and I dont know about shutting down X, but if you press Crtl+Alt and F1 to F6, you will get a command line, you just need to login. Crtl+Alt+F7 will bring you back to X.

On installing the driver, ill do some research, or maybe someone else can help :rolleyes: . I have never really installed a driver before, Ubuntu just worked for me.  :-D

Holy cow! That was amazing! I was having a problem getting Ubuntu to properly [recognize my wireless card](http://www.ubuntuforums.org/showthread.php?t=331096) from the lspci output. After running that command, it showed the correct model instead of "unkown device". Too bad my card doesn't show up in ifconfig >_<

---

### Post by imonlyhuman on 2007-01-06
> **nextse7en said:**
> LOL, now its calling it a.

Dell Wireless 1390 WLAN

But still Broadcom

Cool, from there I would probably try this post.
[http://ubuntuforums.org/showthread.php?t=201902&highlight=ndiswrapper](http://ubuntuforums.org/showthread.php?t=201902&highlight=ndiswrapper)
It will show you how to get ndiswrapper, I haven't used the ndiswrapper before, so I can't exactly help you with that.

But first I would go into System>Admin>Networking, and see if your card shows up.
If it does, then you may have the driver working already. Now that your pc recognizes the card, you should be able to get it working. If you need wpa support, I personally think wpa_supplicant is way too confusing, struggled with it for a while. There is an easier method.
Through synaptic, install network-manager-gnome, and by right (not left) clicking on it, you should be brought to a list of available wireless networks

---

