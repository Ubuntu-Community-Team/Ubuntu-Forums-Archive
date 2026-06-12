---
title: "understanding Ubuntu/linux"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by High Mage on 2007-11-02
hello,

Im new to Ubuntu and i saw some guides in the past 3 days.
I noticed many linux terminology that i didnt quite understand from the guides that this forum provides but im still clueless from how Ubuntu works from "behind".

1 - I notice that GNOME is a desktop interface? so what distro's do is just for kernel development (the complicated code behind)?

2 - also i noticed that Ubuntu has 3 ways of making installations:
     -the package way - whats a package anyway? i never saw that explained anywhere (probably im not a good searcher) that uses some sort of sources.list to get updates? or it also does install it and run it immediatly in the OS?
     -i think the second one is the binary way?
     -the 3rd one i cant even remember but i do know theres a third.

3 - Also how can u manage to memorize so many commands? is there a organized way to understand them?

4 - Another complicated thing that i am trying to understand in this 3 days is how can i install drivers for my laptop.. currently i dont have any sound..and i am unsure how i can manage my hardware..if there is some commands that would help me list and install the drivers on them it would be great :)

5 - Another thing is file conversion..i want to migrate from windows to ubuntu (i am in Ubuntu already) i want to convert files that doesnt work in here..whats the best way to do it?

6 - I wanted to know what programs i dont use anymore or things that i installed badly and remove them..how can i know that?

i wanted to suggest a way of how the guides are made, they are really good by the way but only for people that are already familiar with linux..if you are completly new you get all confused and have a feeling of "why did i do this command for?what it do exactly? How can i tell this isnt a virus?" Probably you guys dont have much time to make more detailed guides and probably its just me that i am a bad searcher..either way im still too much clueless how linux/Ubuntu works. :s

P.S. And please, if your just giving me more commands to do i would still be clueless even if i make it work like i want..i want to understand so i can do things better and not ask same questions over and over again and annoy you guys out. if i understand better someday i can help other people with problems in this wonderful community :)

Thanks in advance :)

---

### Post by Frak on 2007-11-02
> **High Mage said:**
> hello,

Im new to Ubuntu and i saw some guides in the past 3 days.
I noticed many linux terminology that i didnt quite understand from the guides that this forum provides but im still clueless from how Ubuntu works from "behind".

1 - I notice that GNOME is a desktop interface? so what distro's do is just for kernel development (the complicated code behind)?

Gnome is the default for Ubuntu, KDE for Kubuntu, XFCE for Xubuntu, e17 for Elbuntu, Fluxbox for Fluxbuntu, etc.

Could you restate the second part?

> 2 - also i noticed that Ubuntu has 3 ways of making installations:
     -the package way - whats a package anyway? i never saw that explained anywhere (probably im not a good searcher) that uses some sort of sources.list to get updates? or it also does install it and run it immediatly in the OS?
     -i think the second one is the binary way?
     -the 3rd one i cant even remember but i do know theres a third.

-The package way is most prefered. It uses the Update Manager to update the system. Also, the sources.list is held in /etc/apt/ but you really shouldn't mess with this unless you REALLY know what your doing. This is a binary way, the other is via the source code, which is hard to manage.

> 3 - Also how can u manage to memorize so many commands? is there a organized way to understand them?

You just mess with them repeatedly. Just view the other threads in here, and you'll learn all the commands in no time.
> 
4 - Another complicated thing that i am trying to understand in this 3 days is how can i install drivers for my laptop.. currently i dont have any sound..and i am unsure how i can manage my hardware..if there is some commands that would help me list and install the drivers on them it would be great :)

Tell us your hardware and we will help as much as possible.

> 5 - Another thing is file conversion..i want to migrate from windows to ubuntu (i am in Ubuntu already) i want to convert files that doesnt work in here..whats the best way to do it?

Tell us the formats and we will help as much as possible, but this is sketchy.

> 6 - I wanted to know what programs i dont use anymore or things that i installed badly and remove them..how can i know that?

Applications->Add/Remove

> i wanted to suggest a way of how the guides are made, they are really good by the way but only for people that are already familiar with linux..if you are completly new you get all confused and have a feeling of "why did i do this command for?what it do exactly? How can i tell this isnt a virus?" Probably you guys dont have much time to make more detailed guides and probably its just me that i am a bad searcher..either way im still too much clueless how linux/Ubuntu works. :s

If you can find a Linux virus, tell me. I haven't seen one.

> P.S. And please, if your just giving me more commands to do i would still be clueless even if i make it work like i want..i want to understand so i can do things better and not ask same questions over and over again and annoy you guys out. if i understand better someday i can help other people with problems in this wonderful community :)

Ask what you need to do, and we'll tell you the command.

---

### Post by jpietari on 2007-11-02
1. Gnome is the equivalent as win32 in Windows.  There is also XFE and KDE.  Distributions take a number of packages (apps) and put them together to make an OS  (Operating System).  They, also, contribute to projects to enhance an OS.  SInce it is open source, these project are eventually incorporated in different distributions.

2. Ubuntu is installed by using a LiveCD.  Maybe other ways exist, but I do not know of them.  The source.lst you are thinking of, are the locations (repositories) where Ubuntu gets its packages.  It is possible for you to update your OS by changing the source.lst to point to the new OS repositories.  This used to be done, but now you can update your OS by using the "Add/Remove..." program.  This program will change your source.lst for you when it upgrades your OS.

3. Search the web, download a book, or use the "man" function on the command line prompt (i.e. man ls).

4. This is hard.  You have to search the web to find out which driver to use.  This typically involves you finding the proper package (driver) and using the command "apt-get install <package>".  The program "Synaptic Package Manager" is GUI for the apt-get command.

5. It depends on what you are converting.  Most of the stuff I have encountered just works under Linux.  Doc, xls, mp3, avi, jpeg, etc.   I recommend switching these formats as you use them and try to use open standards (use odf instead of doc).  There are scripts for migrating things but I've never used them.

6. Things can be added and removed by using "Add/Remove...", "Synaptic Package Manager" or "apt-get remove <package>".  Sometimes you install things outside these program, which usually come with an uninstall script.

---

### Post by SOULRiDER on 2007-11-02
Check out this doc, it explains about packages, tarballs etc.

[https://help.ubuntu.com/community/SoftwarePackagingFormats](https://help.ubuntu.com/community/SoftwarePackagingFormats)

---

### Post by Frak on 2007-11-02
some good sites
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by Frak on 2007-11-02
> **jpietari said:**
> 1. Gnome is the equivalent as win32 in Windows.  There is also XFE and KDE.  Distributions take a number of packages (apps) and put them together to make an OS  (Operating System).  They, also, contribute to projects to enhance an OS.  SInce it is open source, these project are eventually incorporated in different distributions.

2. Ubuntu is installed by using a LiveCD.  Maybe other ways exist, but I do not know of them.  The source.lst you are thinking of, are the locations (repositories) where Ubuntu gets its packages.  It is possible for you to update your OS by changing the source.lst to point to the new OS repositories.  This used to be done, but now you can update your OS by using the "Add/Remove..." program.  This program will change your source.lst for you when it upgrades your OS.

3. Search the web, download a book, or use the "man" function on the command line prompt (i.e. man ls).

4. This is hard.  You have to search the web to find out which driver to use.  This typically involves you finding the proper package (driver) and using the command "apt-get install <package>".  The program "Synaptic Package Manager" is GUI for the apt-get command.

5. It depends on what you are converting.  Most of the stuff I have encountered just works under Linux.  Doc, xls, mp3, avi, jpeg, etc.   I recommend switching these formats as you use them and try to use open standards (use odf instead of doc).  There are scripts for migrating things but I've never used them.

6. Things can be added and removed by using "Add/Remove...", "Synaptic Package Manager" or "apt-get unistall <package>".  Sometimes you install things outside these program, which usually come with an unnstall script.
sudo apt-get **remove** <package>

---

### Post by High Mage on 2007-11-03
oh thx guys this is really helpful :)

ok ill say my specs:
-Useing Ubuntu 7.10 64 bits
-laptop compal (dont know the version)
-intel core2 duo T7700 2.4 GHz (do i need to install drivers for this?)
-Mem 2 gig at 666 MHz i think
-HDD 160 gig SATA
-NVidia 8600GT 512 mb mobile (not sure i installed them correctly..)

i would also like some commands that works the same as in the "device manager" in windows i wanted to see the device name for my sound card since it doesnt work.

thanks in advance :)

---

### Post by Frak on 2007-11-03
> **High Mage said:**
> oh thx guys this is really helpful :)

ok ill say my specs:
-Useing Ubuntu 7.10 64 bits
-laptop compal (dont know the version)
-intel core2 duo T7700 2.4 GHz (do i need to install drivers for this?)
-Mem 2 gig at 666 MHz i think
-HDD 160 gig SATA
-NVidia 8600GT 512 mb mobile (not sure i installed them correctly..)

i would also like some commands that works the same as in the "device manager" in windows i wanted to see the device name for my sound card since it doesnt work.

thanks in advance :)
```
aplay --list-devices
```

---

### Post by High Mage on 2007-11-03
that command only shows me this:

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by Nythain on 2007-11-03
i dont know if its been pointed out... but memorizing so many commands is rather easy, most bash commands are run similarly to what you are trying to do...
cd = change directory
rm = remove
cp = copy
sudo = i like to think of this as super user do, like do stuff as a super user

the list goes on and on and on, but most commands are relatively easy to remember because they all pretty much sound like what you are wanting to do... at least thats how i remember most of them :)

---

### Post by Frak on 2007-11-03
Try these two and post what you see in the Multimedia section
```
lspci -vvnn 
lspnp -v
```

---

### Post by High Mage on 2007-11-03
```
nfcae@nfcae-laptop:~/ndiswrapper-1.49$ lspci -vvnn 
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
        Subsystem: COMPAL Electronics Inc Unknown device [14c0:0025]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
        Latency: 0
        Capabilities: <access denied>

00:01.0 PCI bridge [0604]: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port [8086:2a01] (rev 0c) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: c4000000-c6ffffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
        BridgeCtl: Parity- SERR+ NoISA- VGA+ MAbort- >Reset- FastB2B-
        Capabilities: <access denied>

00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 [8086:2834] (rev 03) (prog-if 00 [UHCI])
        Subsystem: COMPAL Electronics Inc Unknown device [14c0:0025]
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 16
        Region 4: I/O ports at 1800 [size=32]

00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03) (prog-if 00 [UHCI])
        Subsystem: COMPAL Electronics Inc Unknown device [14c0:0025]
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin B routed to IRQ 21
        Region 4: I/O ports at 1820 [size=32]

00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03) (prog-if 20 [EHCI])
        Subsystem: COMPAL Electronics Inc Unknown device [14c0:0025]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin C routed to IRQ 18
        Region 0: Memory at f8404800 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
        Subsystem: COMPAL Electronics Inc Unknown device [14c0:0025]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 20
        Region 0: Memory at f8400000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: bc000000-bfffffff
        Prefetchable memory behind bridge: 00000000cc000000-00000000cdffffff
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
        Capabilities: <access denied>

00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        I/O behind bridge: 00004000-00004fff
        Memory behind bridge: f0000000-f3ffffff
        Prefetchable memory behind bridge: 00000000fa000000-00000000fbffffff
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
        Capabilities: <access denied>

00:1c.2 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 [8086:2843] (rev 03) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
        I/O behind bridge: 00005000-00005fff
        Memory behind bridge: f4000000-f7ffffff
        Prefetchable memory behind bridge: 00000000fc000000-00000000fdffffff
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
        Capabilities: <access denied>

00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 03) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
        I/O behind bridge: 00006000-00006fff
        Memory behind bridge: b4000000-b7ffffff
        Prefetchable memory behind bridge: 00000000c8000000-00000000c9ffffff
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
        Capabilities: <access denied>

00:1c.4 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 [8086:2847] (rev 03) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=0
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
        Capabilities: <access denied>

00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 03) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Bus: primary=00, secondary=0c, subordinate=0c, sec-latency=0
        Memory behind bridge: f8000000-f80fffff
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR+ <PERR-
        BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
        Capabilities: <access denied>

00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03) (prog-if 00 [UHCI])
        Subsystem: COMPAL Electronics Inc Unknown device [14c0:0025]
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 23
        Region 4: I/O ports at 1840 [size=32]

00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03) (prog-if 00 [UHCI])
        Subsystem: COMPAL Electronics Inc Unknown device [14c0:0025]
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin B routed to IRQ 19
        Region 4: I/O ports at 1860 [size=32]

00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03) (prog-if 00 [UHCI])
        Subsystem: COMPAL Electronics Inc Unknown device [14c0:0025]
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin C routed to IRQ 18
        Region 4: I/O ports at 1880 [size=32]

00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03) (prog-if 20 [EHCI])
        Subsystem: COMPAL Electronics Inc Unknown device [14c0:0025]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 23
        Region 0: Memory at f8404c00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3) (prog-if 01 [Subtractive decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Bus: primary=00, secondary=0e, subordinate=0e, sec-latency=32
        Memory behind bridge: f8100000-f81fffff
        Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
        Capabilities: <access denied>

00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Capabilities: <access denied>

00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03) (prog-if 8a [Master SecP PriP])
        Subsystem: COMPAL Electronics Inc Unknown device [14c0:0025]
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 19
        Region 0: I/O ports at 01f0 [size=8]
        Region 1: I/O ports at 03f4 [size=1]
        Region 2: I/O ports at 0170 [size=8]
        Region 3: I/O ports at 0374 [size=1]
        Region 4: I/O ports at 18a0 [size=16]

00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 03) (prog-if 01 [AHCI 1.0])
        Subsystem: COMPAL Electronics Inc Unknown device [14c0:0025]
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin B routed to IRQ 19
        Region 0: I/O ports at 18d8 [size=8]
        Region 1: I/O ports at 18cc [size=4]
        Region 2: I/O ports at 18d0 [size=8]
        Region 3: I/O ports at 18c8 [size=4]
        Region 4: I/O ports at 18e0 [size=32]
        Region 5: Memory at f8404000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
        Subsystem: COMPAL Electronics Inc Unknown device [14c0:0025]
        Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin C routed to IRQ 10
        Region 0: Memory at 88000000 (32-bit, non-prefetchable) [size=256]
        Region 4: I/O ports at 1c00 [size=32]

01:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce 8600M GT [10de:0407] (rev a1) (prog-if 00 [VGA])
        Subsystem: COMPAL Electronics Inc Unknown device [14c0:0025]
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 16
        Region 0: Memory at c6000000 (32-bit, non-prefetchable) [size=16M]
        Region 1: Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Region 3: Memory at c4000000 (64-bit, non-prefetchable) [size=32M]
        Region 5: I/O ports at 2000 [size=128]
        Capabilities: <access denied>

04:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express [14e4:1693] (rev 02)
        Subsystem: COMPAL Electronics Inc Unknown device [14c0:0025]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR+ <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 17
        Region 0: Memory at f0000000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

08:00.0 Memory controller [0580]: Intel Corporation Turbo Memory Controller [8086:444e] (rev 01)
        Subsystem: Intel Corporation Turbo Memory Controller [8086:444e]
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 10
        Region 0: Memory at b4000000 (32-bit, non-prefetchable) [size=1K]
        Region 2: I/O ports at 6000 [size=128]
        [virtual] Expansion ROM at c8000000 [disabled] [size=64K]
        Capabilities: <access denied>

0c:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection [8086:4229] (rev 61)
        Subsystem: Intel Corporation Unknown device [8086:1101]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR+ <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 17
        Region 0: Memory at f8000000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>

0e:06.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05) (prog-if 10 [OHCI])
        Subsystem: COMPAL Electronics Inc Unknown device [14c0:0025]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (500ns min, 1000ns max), Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 22
        Region 0: Memory at f8100000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

0e:06.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
        Subsystem: COMPAL Electronics Inc Unknown device [14c0:0025]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64, Cache Line Size: 64 bytes
        Interrupt: pin B routed to IRQ 23
        Region 0: Memory at f8100800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

0e:06.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
        Subsystem: COMPAL Electronics Inc Unknown device [14c0:0025]
        Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin B routed to IRQ 10
        Region 0: Memory at f8100c00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

nfcae@nfcae-laptop:~/ndiswrapper-1.49$ lspnp -v
The program 'lspnp' can be found in the following packages:
 * pnpbios-tools
 * pnputils
Try: sudo apt-get install <selected package>
bash: lspnp: command not found
nfcae@nfcae-laptop:~/ndiswrapper-1.49$ sudo apt-get install lspnp
[sudo] password for nfcae:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package lspnp

```

tried to install with sudo apt-get install lspnp but i guess it didnt work..why does that happen? where does he get that information from? :s

---

### Post by sandysandy on 2007-11-03
i think these links are wonderful.

can anyone tell me how one can bookmark a particular thread. is it possible to do so within ones profile so that moment you sign in  you can see the important threads that are of use to  a particular user.

thanks.:)

---

### Post by jpietari on 2007-11-03
The device manager screen (like windows) is under System -> Preferences -> Hardware Information.

---

### Post by sandysandy on 2007-11-03
> **jpietari said:**
> The device manager screen (like windows) is under System -> Preferences -> Hardware Information.

thanx.

is it also possible to bookmark it within the forum. (i use livecd so moment i reboot all my bookmarks would be of no use)

regards

---

### Post by High Mage on 2007-11-03
Yeah i found out that feature..but i still dont know what to do to make my sound to work :s
I think im useing some sort of intel sound card..i went to their site looking for their drivers..but i only saw Windows drivers :(

---

### Post by pashashome on 2007-11-03
You may want to check out this [http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/]("http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/")

---

### Post by SQuark on 2007-11-03
> **sandysandy said:**
> i think these links are wonderful.

can anyone tell me how one can bookmark a particular thread. is it possible to do so within ones profile so that moment you sign in  you can see the important threads that are of use to  a particular user.

thanks.:)

At the top of this page, click on "Thread Tools>Subscribe to this Thread".

You can now click on "User CP" and find out when new posts are made to this thread, or any other thread you're subscribed to.

---

### Post by Sbarton on 2007-11-03
> **sandysandy said:**
> thanx.

is it also possible to bookmark it within the forum. (i use livecd so moment i reboot all my bookmarks would be of no use)

regards
Hi sandysandy, you could use your 'user control panel' in Ubuntu Forums to subscibe to various posts, that way you can go back to some links. This is one way, maybe it might help,
regards

---

### Post by High Mage on 2007-11-03
Im really clueless on what to do is this impossible to fix? :(

---

### Post by Frak on 2007-11-03
> **High Mage said:**
> Im really clueless on what to do is this impossible to fix? :(
Did you follow the sites instructions then reboot. This is a kernel problem where the kernel froze before the driver was fully added.

---

### Post by DonLorenzo on 2007-11-03
My comment here is a bit orthogonal to your need to get things working and to learn how to use it. So, bear with me here ...

First! Slow down. Though it is hard to know your starting point, I'd speculate that you are a "newbie". That in itself is not a problem: everybody's gotta start somewhere. You'll get it in time. The point is: don't expect to get it all at once. Again, from your apparent "newbie" station, figure on a few months to a year (depending ...) before you have everything you have (working box, skills, conversions, ...) on your windows box.For example, I started my Linux conversion with the luxury of having 2 computers to mess with: one exclusively Linux while the other ran my "legacy" Windows crap. I started in April (2007) and did not convert to Linux full time until August (2007).

Keep a journal of your activities and progress. Nothing improves learning quite like planning on paper then doing a brian dump after you've executed the plan. You'll be glad you did when you are done. Remember! There's the next release you have to deal with. Your notes will serve you well when doing the upgrade.

OK, if you have only one box to work with, make it dual boot. Keep Windows going as your primary platform until you feel confident that you can make the switch. Note that I run Ubuntu full time, but still run Win2K in a virtual machine for Quicken. The sad news is that Quicken files are not easily (if at all) convertable to some Linux equivalent. I'm prepared to continue with Windows in a virtual machine for the foreseeable future.

Do things one step at the time. The first step should be to get a working Linux configuration. As a suggestion:
[LIST]
[*]Get Linux installed, bare bones, from distribution media.
[*]Evaluate what works (hardware wise) and what does not.
[*]Search (Google, Ubuntuforums, ...) for solutions to your hardware compatibility problems. Fix same. ... one at the time.
[/LIST]
Now, about converting your Windows applications to Linux:
[LIST]
[*]List all the Windows applications you've come to depend upon.
[*]Search for Linux equivalents of those applications.
[*]For each Windows application determination the conversion steps you need to do and in a test only environment, convert your data to the Linux equivalent. Some Linux packages have conversion tools, some do not. Depending on your skills, you may have to write a custom conversion utility or get someone else to do it for you ($$$). Know that whatever Linux application you use to replace the Windows application may not have every function you want or need. This takes time to discover, evaluate and solve. Take your time.
[*[Evaluate the Linux application to assure that it is, indeed, a suitable replacement for the Windows application. If not, choose another and repeat the evaluation.
[*]If there is no suitable Linux replacement for your Windows application, decide if you're gonna continue dual-boot or use some virtualization method to run Windows. Implement same.
[*]Now, you can convert or port your live applaction data to your new Linux environment.
[*]Remember to do backups! Test your restore procedure. If it hasn't been tested, it's guaranteed not to work.
[/LIST]
About learning commands. Buy yourself a good book. A good newbie book might be appropriate. Without having specific knowledge of it, I've heard others recommend: Matt Welsh, et al, *_"Running Linux"_*, O'Reill, 5th ed.

I also believe that all but the most casual user of Linux needs some understanding of how Linux works. You don't have to be a programmer, just conceptually understand processes, filesystems, memory management and the like. It's a good idea to unserstand the init process, how sub-systems are started, stopped and restarted. That will come as you learn other parts of Linux.

I would also tell you:
[LIST]
[*]Get involved with your local Linux User Group (LUG).
[*]Read voratiously the Ubuntu documentation.
[*]Ask others for recommendations on books, gurus, and other resources.
[/LIST]
I feel your frustration. Just know that it's gonna take a while before you have it all under control and before you have confidence that you can tackle any problem you run into. You are not alone! The getting started problems are just one of those things you will have to struggle through. When you have mastered the basics, you will feel so much better and wonder How TF did you ever tolerate Windows as long as you did.

Remember too: Give Back. You got help here. When you're ready, give help to those struggling with the same getting started challenges you are facing today.

Hang in there. Have patience. You'll get there.

HTH.

---

### Post by High Mage on 2007-11-03
I tried getting those drivers that the nvidia site tells me to: [http://www.nvidia.com/object/linux_nforce_1.23.html](http://www.nvidia.com/object/linux_nforce_1.23.html)

though they dont let me download the sound drivers..any ideas on how i can get them?
please its been 4 days that i dont have a single sound :(

---

### Post by High Mage on 2007-11-03
Oh i didnt see that last post there..yeah ill take that into account, thanks a lot DonLorenzo :)

*EDIT* lol i didnt know there was more posts behind, sry ill look at all you guys are telling me to do :)

---

### Post by High Mage on 2007-11-03
I notice when i reboot that the kernel gives me a "failure warning" i dont know what it says  because the comp starts too quick :s.. I even tried hitting the "pause" button to see if he stopped so i could see the error but no use...so i guess i have to uninstall and install those same drivers that site gives me? (this one: [http://lddubeau.com/avaktavyam/linux-on-a-compal-ifl90/#gutsysound](http://lddubeau.com/avaktavyam/linux-on-a-compal-ifl90/#gutsysound) )

*EDIT* sry for the triple post :s

---

### Post by SQuark on 2007-11-03
> **High Mage said:**
> I tried getting those drivers that the nvidia site tells me to: [http://www.nvidia.com/object/linux_nforce_1.23.html](http://www.nvidia.com/object/linux_nforce_1.23.html)

though they dont let me download the sound drivers..any ideas on how i can get them?
please its been 4 days that i dont have a single sound :(

This may not help you one bit, but it's worth a try. It seems to work for a variety of people with different sound problems under Gutsy (including me).

```
sudo apt-get install linux-backports-modules-generic
```

---

### Post by High Mage on 2007-11-03
What that command does exactly?

---

### Post by SQuark on 2007-11-03
As far as I understand, it installs a newer version (one that's actually being prepared for the next Ubuntu release) of several drivers. There may a few bugs in the sound driver that's being shipped with Gutsy.

---

### Post by High Mage on 2007-11-03
erm that command made my keyboard not to work when i rebooted..now how can i fix that? (im on another comp)

---

### Post by High Mage on 2007-11-03
Ok is there a way i can remove all unnecessary packages and only have the necessary ones? also i wanted to reinstall everything back..how can i do that? (i still cant put the login pass in my laptop because the keyboard doesnt respond :()

---

### Post by High Mage on 2007-11-03
I already tried to do
```
sudo apt-get remove linux-backport-modules-generic
```
but he doesnt recognize it :s

---

