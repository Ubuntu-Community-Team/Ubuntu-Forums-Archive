---
title: "NEED HELP on changing INTERNAL WIFI CARD"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by rawrico on 2008-01-11
1st of all,i have no idea got people do this or not...

My laptop model is Compaq V3203AU
chipset is nforce of course,cause of the proccessor is AMD type...

here is my question,i hope some one can help me work on this
I recently bought a MiniPCI,or should i say Mini-PCI-E,
Cause of for new type of laptop....

the Mini PCI-E i bought is intel 3954 chipset,(if you need more info,i will post later)
the one that maintain on my laptop is Broadcom,A/B/G/Draft-N.

SO,is it posible to change the card just like that,and nothing to do just install driver???

cause i can't detect the 3954 intel card even in WindowXP or VISTA,of course even my ubuntu also...

Please help me on this issue....Thank you
Below is the list that i put "LSPCI" in terminal

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
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)
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
01:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
05:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
05:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
05:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
05:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

---

### Post by warbread on 2008-01-11
I apologize, but I'm having trouble understanding what you're trying to ask.  You're saying that your Express 54 or 34 card isn't being recognized?

Is there anything else that **does **work in your card slot?  Do you have it disabled in the BIOS for some odd reason?

---

### Post by rawrico on 2008-01-11
> **warbread said:**
> I apologize, but I'm having trouble understanding what you're trying to ask.  You're saying that your Express 54 or 34 card isn't being recognized?

Is there anything else that **does **work in your card slot?  Do you have it disabled in the BIOS for some odd reason?

err..........
Sorry for that i confusing you
what am i asking is,my internal WIFI-CARD
here is the PICTURE(This is my remain one wifi card)
[IMG]http://img245.imageshack.us/img245/5627/dsc00373ok1.jpg[/IMG]

what i'm asking is,if i'm change to 3954 INTEL wifi card
logicaly should works,cause connector are correct(MMCX),the slot also are correct....
but can't detect at all

---

### Post by warbread on 2008-01-11
This is unfortunate.

It seems that Compaq is part of a project called the [Trusted Computing Platform Alliance]("http://en.wikipedia.org/wiki/Trusted_Computing_Platform_Alliance").  What this means is that the BIOS has a list of devices that it will **allow** to work with the computer, and everything else is not allowed.  

You might be able to flash the BIOS.  [This guy]("http://www.richud.com/HP-Pavilion-104-Bios-Fix/") did something similar on his HP Pavillion.  Other than that, it looks like you might be stuck with Broadcom.  :(

Also, if you don't mind me asking rawrico, where are you from and what's your native language?  I'm just a curious linguist.

---

### Post by rawrico on 2008-01-11
> **warbread said:**
> This is unfortunate.

It seems that Compaq is part of a project called the [Trusted Computing Platform Alliance]("http://en.wikipedia.org/wiki/Trusted_Computing_Platform_Alliance").  What this means is that the BIOS has a list of devices that it will **allow** to work with the computer, and everything else is not allowed.  

You might be able to flash the BIOS.  [This guy]("http://www.richud.com/HP-Pavilion-104-Bios-Fix/") did something similar on his HP Pavillion.  Other than that, it looks like you might be stuck with Broadcom.  :(

Also, if you don't mind me asking rawrico, where are you from and what's your native language?  I'm just a curious linguist.

well
i'm not mind every one ask me where i'm from
i'm from Malaysia,sorry for those broken english i had from my "finger"

by the way,thanks for the info

---

