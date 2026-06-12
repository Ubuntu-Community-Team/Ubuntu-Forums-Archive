---
title: "install software from cd..."
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by ninja senses on 2007-12-20
I have a tv tuner card for my computer and I just installed ubuntu.  I wanted to try and use it on here so I got the software disc and popped it in and I am clueless on how to install it.  I tried just to double click it and I get "No application suitable for automatic installation is available for handling this kind of file."  SO then i went to add/remove applications but I dont see any options for the cd-rom, help?

ps - 6 min left in the cavs game:mad:

---

### Post by gletob on 2007-12-20
thats cause that cd has drivers for windows could you please give me some info about the TV Tuner

---

### Post by PmDematagoda on 2007-12-20
What is the extension of the file you are trying to install?

---

### Post by ninja senses on 2007-12-20
> **gletob said:**
> thats cause that cd has drivers for windows could you please give me some info about the TV Tuner

i only have the cd, it says ati catalyst software, on the right side it has these numbers: 200, 180-V01069-200

---

### Post by logos34 on 2007-12-20
it's probably sw for windows, so forget it.  Most tv tuner cards don't even support linux.  But that doesn't mean you can't find drivers to run it in ubuntu.  Check out the MythTV guides in the community docs.

here's just one:
[https://help.ubuntu.com/community/MythTV/Install/Gutsy/Tuners](https://help.ubuntu.com/community/MythTV/Install/Gutsy/Tuners)

---

### Post by ninja senses on 2007-12-20
i just checked ati's website and it says its only compatable with windows OS:(

---

### Post by gletob on 2007-12-20
ati is not very linux friendly especially since amd took over but you should still look for drivers is it a PCI card or Usb

---

### Post by ninja senses on 2007-12-20
> **gletob said:**
> ati is not very linux friendly especially since amd took over but you should still look for drivers is it a PCI card or Usb

PCI hmm...ill try to google it

---

### Post by gletob on 2007-12-20
if its PCI type lspci and post output 
for usb type lsusb and post output

---

### Post by ninja senses on 2007-12-20
> **gletob said:**
> if its PCI type lspci and post output 
for usb type lsusb and post output

00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev c1)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
00:05.0 Multimedia audio controller: nVidia Corporation nForce Audio Processing Unit (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
00:0c.0 PCI bridge: nVidia Corporation nForce2 PCI Bridge (rev a3)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
01:07.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
01:0a.0 Ethernet controller: Atheros Communications, Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
01:0b.0 RAID bus controller: Silicon Image, Inc. SiI 3112 [SATALink/SATARaid] Serial ATA Controller (rev 02)
02:01.0 Ethernet controller: 3Com Corporation 3C920B-EMB Integrated Fast Ethernet Controller [Tornado] (rev 40)
03:00.0 VGA compatible controller: nVidia Corporation NV31 [GeForce FX 5600] (rev a1)
sense@sense-ubuntu:~$

---

### Post by ninja senses on 2007-12-20
> **ninja senses said:**
> 00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev c1)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
00:05.0 Multimedia audio controller: nVidia Corporation nForce Audio Processing Unit (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
00:0c.0 PCI bridge: nVidia Corporation nForce2 PCI Bridge (rev a3)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
01:07.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
01:0a.0 Ethernet controller: Atheros Communications, Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
01:0b.0 RAID bus controller: Silicon Image, Inc. SiI 3112 [SATALink/SATARaid] Serial ATA Controller (rev 02)
02:01.0 Ethernet controller: 3Com Corporation 3C920B-EMB Integrated Fast Ethernet Controller [Tornado] (rev 40)
03:00.0 VGA compatible controller: nVidia Corporation NV31 [GeForce FX 5600] (rev a1)
sense@sense-ubuntu:~$

i dont even see it in there:confused:

i think i can get the drivers here :[http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html) but im not sure which on i got

---

### Post by gletob on 2007-12-21
are you sure its PCI if its not type lsusb and post output

---

### Post by ninja senses on 2007-12-21
> **gletob said:**
> are you sure its PCI if its not type lsusb and post output

positive

---

### Post by ninja senses on 2008-01-09
I finally figured out a solution, all I had to do was download tvtime and it worked instantly

---

