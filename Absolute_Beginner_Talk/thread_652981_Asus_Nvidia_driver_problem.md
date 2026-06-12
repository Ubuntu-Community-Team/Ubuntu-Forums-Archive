---
title: "Asus Nvidia driver problem"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by Fonikar on 2007-12-29
HI there

Just embarking on my first Ubuntu install and can't seem to get the network going. I am guessing it's because I need to install the mobo drivers.

I've got an Asus M2NPV-VM board and I've downloaded the driver packages from the Asus site. These are .run files and I've been trying to run them from double clicking the file (on the cd rom). Is this right?

the problem is that is says that it seems to try to run, but then comes up with a window that says: Could not open the file ...................gedit has not been able to detect the character coding................

any ideas?

Chris

---

### Post by Fonikar on 2007-12-29
btw I'm using Feisty 7.04

hopefully someone can give me some clues.

Thanks

Chris

---

### Post by overdrank on 2007-12-29
> **Fonikar said:**
> btw I'm using Feisty 7.04

hopefully someone can give me some clues.

Thanks

Chris

Hi and could you post the link to what you are trying to install and also post the output of the command in the terminal ```
lspci
``` you can just copy and paste, the terminal is located under applications, accessories. That command will tell us the hardware on the system and maybe we can help.

---

### Post by Fonikar on 2007-12-29
Ok, no problem.

THe files are located here:

[http://support.asus.com/download/download.aspx?model=M2NPV-VM&SLanguage=en-us](http://support.asus.com/download/download.aspx?model=M2NPV-VM&SLanguage=en-us)

under the drivers tab with OS set to Linux.


and this is the output of the lspci command.

Thanks again in advance

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
00:05.0 VGA compatible controller: nVidia Corporation C51PV [GeForce 6150] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 RAID bus controller: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
04:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
04:09.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
04:09.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
04:09.4 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [IR Port] (rev 05)

---

### Post by overdrank on 2007-12-29
Ok please correct me if I wrong but I have looked at the lspci output and I do not see a network card. Are you sure it is enabled in bios? As for the drivers 
 	NVIDIA Chipset 32/64bit Linux Driver install package for kernel 2.4 and 2.6
I have no idea but for  the graphics the restricted drivers should work well.

---

### Post by Fonikar on 2007-12-29
There is this line in the output

00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)

the mobo has integrated network adaptor.

I am figuring tHe drivers should work ok, but I can't seem to get them to run. Am I doing it in the correct way - ie should I be installing it from terminal using some sort of extra commands? (I'm very new to this, so assume I know nothing.)

THanks

---

### Post by overdrank on 2007-12-29
> **Fonikar said:**
> There is this line in the output

00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)

the mobo has integrated network adaptor.

I am figuring tHe drivers should work ok, but I can't seem to get them to run. Am I doing it in the correct way - ie should I be installing it from terminal using some sort of extra commands? (I'm very new to this, so assume I know nothing.)

THanks

:shock: Man I need glasses. You are right and the drivers you linked are not for the network I believe. [-o< And I am not the greatest at networking so I don't know how to install those drivers and maybe someone else will come along. :KS

---

### Post by Fonikar on 2007-12-29
THanks anyway.

I think the chipset drivers do include the Ethernet drivers as it's covered in the release notes. I think the problem is more likely that I'm trying to install it the wrong way.

Thanks again

Chris

---

