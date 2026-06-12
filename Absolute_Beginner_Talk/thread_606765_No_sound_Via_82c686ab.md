---
title: "No sound Via 82c686a/b"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by dantienn on 2007-11-08
**This post could be related to an Ubuntu bug filed at**: [http://hwdb.ubuntu.com/?xml=e58c8709c6c02fdde526a6c0f92add3e](http://hwdb.ubuntu.com/?xml=e58c8709c6c02fdde526a6c0f92add3e) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				**This post could be related to an Ubuntu bug filed at**: [http://hwdb.ubuntu.com/?xml=e58c8709c6c02fdde526a6c0f92add3e](http://hwdb.ubuntu.com/?xml=e58c8709c6c02fdde526a6c0f92add3e) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi
I have just installed Kubuntu 7.10 from live cd and i just love how smooth and nice it is. I now wonder whay peaople bother using windows :)


I stumbled on one problem that i dont know how to fix. there is no sound. I noticed that thre are a lot of people helping newbees, so i post my problem here.
i have runed all availeble updates.

I dont know if it means anyything, but i posting here the command lspci -vvx
```
00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 81)
        Subsystem: ASUSTeK Computer Inc. Unknown device 8041
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Steping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbor- <MAbort+ >SERR- <PERR+
        Latency: 40
        Region 0: Memory at fc000000 (32-bit, prefetchable) [size=32M]
        Capabilities: <access denied>
00: 06 11 05 03 06 00 10 a2 81 00 00 06 00 28 00 00
10: 08 00 00 fc 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 43 10 41 80
30: 00 00 00 00 a0 00 00 00 00 00 00 00 00 00 00 00

00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP] (prog-f 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Steping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbor- <MAbort+ >SERR- <PERR-
        Latency: 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: bf000000-bfffffff
        Prefetchable memory behind bridge: c0000000-fbffffff
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort-<MAbort- <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA- VGA+ MAbort- >Reset- FastB2B-
        Capabilities: <access denied>
00: 06 11 05 83 07 00 30 22 00 00 04 06 00 00 01 00
10: 00 00 00 00 00 00 00 00 00 01 01 00 d0 d0 00 00
20: 00 bf f0 bf 00 c0 f0 fb 00 00 00 00 43 10 41 80
30: 00 00 00 00 80 00 00 00 00 00 00 00 00 00 08 00

00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 4)
        Subsystem: ASUSTeK Computer Inc. Unknown device 80e7
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Steping+ SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbor- <MAbort- >SERR- <PERR-
        Latency: 0
        Capabilities: <access denied>
00: 06 11 86 06 87 00 10 02 40 00 01 06 00 00 80 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 43 10 e7 80
30: 00 00 00 00 c0 00 00 00 00 00 00 00 00 00 00 00

00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/AC PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Steping+ SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbor- <MAbort- >SERR- <PERR-
        Latency: 32
        Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size8]
        Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size1]
        Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size8]
        Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable) [size1]
        Region 4: I/O ports at b800 [size=16]
        Capabilities: <access denied>
00: 06 11 71 05 87 00 90 02 06 8a 01 01 00 20 00 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 01 b8 00 00 00 00 00 00 00 00 00 00 00 00 00 00
30: 00 00 00 00 c0 00 00 00 00 00 00 00 00 00 00 00

00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controlle (rev 16) (prog-if 00 [UHCI])
        Subsystem: First International Computer, Inc. VA-502 Mainboard
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Steping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbor- <MAbort- >SERR- <PERR-
        Latency: 32, Cache Line Size: 32 bytes
        Interrupt: pin D routed to IRQ 9
        Region 4: I/O ports at b400 [size=32]
        Capabilities: <access denied>
00: 06 11 38 30 17 00 10 02 16 00 03 0c 08 20 00 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 01 b4 00 00 00 00 00 00 00 00 00 00 25 09 34 12
30: 00 00 00 00 80 00 00 00 00 00 00 00 09 04 00 00

00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controlle (rev 16) (prog-if 00 [UHCI])
        Subsystem: First International Computer, Inc. VA-502 Mainboard
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Steping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbor- <MAbort- >SERR- <PERR-
        Latency: 32, Cache Line Size: 32 bytes
        Interrupt: pin D routed to IRQ 9
        Region 4: I/O ports at b000 [size=32]
        Capabilities: <access denied>
00: 06 11 38 30 17 00 10 02 16 00 03 0c 08 20 00 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 01 b0 00 00 00 00 00 00 00 00 00 00 25 09 34 12
30: 00 00 00 00 80 00 00 00 00 00 00 00 09 04 00 00

00:07.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
        Subsystem: ASUSTeK Computer Inc. Unknown device 80e7
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Steping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbor- <MAbort- >SERR- <PERR-
        Interrupt: pin ? routed to IRQ 9
        Capabilities: <access denied>
00: 06 11 57 30 00 00 90 02 40 00 80 06 00 00 00 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 43 10 e7 80
30: 00 00 00 00 68 00 00 00 00 00 00 00 00 00 00 00

00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 AudioController (rev 50)
        Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Steping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbor- <MAbort- >SERR- <PERR-
        Interrupt: pin C routed to IRQ 5
        Region 0: I/O ports at a800 [size=256]
        Region 1: I/O ports at a400 [size=4]
        Region 2: I/O ports at a000 [size=4]
        Capabilities: <access denied>
00: 06 11 58 30 01 00 10 02 50 00 01 04 00 00 00 00
10: 01 a8 00 00 01 a4 00 00 01 a0 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
30: 00 00 00 00 c0 00 00 00 00 00 00 00 05 03 00 00

00:0d.0 Network controller: RaLink Wireless PCI Adapter RT2400 / RT2460
        Subsystem: CNet Technology Inc Unknown device 0011
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Steping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort-<MAbort- >SERR- <PERR-
        Latency: 32, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 11
        Region 0: Memory at be800000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>
00: 14 18 01 01 16 00 10 04 00 00 80 02 10 20 00 00
10: 00 00 80 be 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 01 06 00 00 71 13 11 00
30: 00 00 00 00 40 00 00 00 00 00 00 00 ff 01 00 00

00:0e.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/813C+ (rev 10)
        Subsystem: Realtek Semiconductor Co., Ltd. RT8139
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Steping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbor- <MAbort- >SERR- <PERR-
        Latency: 32 (8000ns min, 16000ns max)
        Interrupt: pin A routed to IRQ 11
        Region 0: I/O ports at 9400 [size=256]
        Region 1: Memory at be000000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
00: ec 10 39 81 07 00 90 02 10 00 00 02 00 20 00 00
10: 01 94 00 00 00 00 00 be 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 ec 10 39 81
30: 00 00 00 00 50 00 00 00 00 00 00 00 ff 01 20 40

01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600] prog-if 00 [VGA])
        Subsystem: PC Partner Limited Unknown device 7c20
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Steping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbor- <MAbort- >SERR- <PERR-
        Latency: 64 (2000ns min), Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 11
        Region 0: Memory at e0000000 (32-bit, prefetchable) [size=256M]
        Region 1: I/O ports at d800 [size=256]
        Region 2: Memory at bf800000 (32-bit, non-prefetchable) [size=64K]
        Expansion ROM at dffe0000 [disabled] [size=128K]
        Capabilities: <access denied>
00: 02 10 50 41 07 00 b0 02 00 00 00 03 08 40 80 00
10: 08 00 00 e0 01 d8 00 00 00 00 80 bf 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 4b 17 20 7c
30: 00 00 fe df 58 00 00 00 00 00 00 00 0b 01 08 00

01:00.1 Display controller: ATI Technologies Inc RV350 AP [Radeon 9600] (Secondry)
        Subsystem: PC Partner Limited Unknown device 7c21
        Control: I/O- Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Steping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbor- <MAbort- >SERR- <PERR-
        Latency: 64 (2000ns min), Cache Line Size: 32 bytes
        Region 0: Memory at c0000000 (32-bit, prefetchable) [disabled] [size=25M]
        Region 1: Memory at bf000000 (32-bit, non-prefetchable) [disabled] [siz=64K]
        Capabilities: <access denied>
00: 02 10 70 41 04 00 b0 02 00 00 80 03 08 40 00 00
10: 08 00 00 c0 00 00 00 bf 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 4b 17 21 7c
30: 00 00 00 00 50 00 00 00 00 00 00 00 ff 00 08 00

```
If there is other commands that shows other importan information just write to me and i will post it.

---

### Post by unclepike on 2007-11-08
I had the same problem. Right click the speaker icon on the toolbar. Choose preferences.Check to make sure the device listed is the same as the soundcard you are using. If not, click the arrow and change it. Click close. Now click "system" on the toolbar, then "preferences", then "sound". Make sure default soundcard is the same as your soundcard also. Make sure enable software sound mixing is enabled and also play system sounds. This may be a good time to setup some of these sounds also, if you haven't already. Reboot. 
  By the way, I'm an old hand at windows but am also an " almost newbie" to linux. I guess I had better add one more thing. I'm using 6.0 ubuntu instead of the 7.0 version. The CD they sent me also had a "no sound problem". I reverted to 6.0 and did what was stated above and now the sound is fine. I hope this helps.

---

### Post by dantienn on 2007-11-08
Thanks for the help unclepike, but sadly there is diffrent GUI from ubuntu and Kubuntu. So i cant follow your clicks... :P
But i only have 1 soundcard, and its integrated to the mainboard. 

**** List of PLAYBACK Hardware Devices ****
card 0: rev50 [VIA 82C686A/B rev50], device 0: VIA 82C686A/B rev50 [VIA 82C686A/B rev50]
Subdevices: 1/1
Subdevice #0: subdevice #0


&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;[AlsaMixer v1.0.14 (Press Escape to quit)]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: VIA 82C686A/B rev50                                                    &#9474;
&#9474; Chip: Realtek ALC200,200P rev 0                                              &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: Master [dB gain=-10.50, -10.50]                                        &#9474;
&#9474;                                                                              &#9474;
&#9474;    &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;               &#9484;&#9472;&#9472;&#9488;              &#9474;
&#9474;    &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;               &#9474;  &#9474;              &#9474;
&#9474;    &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;               &#9474;  &#9474;              &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;              >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;              >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;              >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;              >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;              >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;              >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;              &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;              &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;    pre 3D    &#9474;
&#9474;    &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;      &#9500;&#9472;&#9472;&#9508;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;      &#9484;&#9472;&#9472;&#9488;     &#9500;&#9472;&#9472;&#9508;              &#9474;
&#9474;    &#9474;OO&#9474;     &#9474;OO&#9474;      &#9474;OO&#9474;                        &#9474;OO&#9474;     &#9474;OO&#9474;              &#9474;
&#9474;    &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;      &#9492;&#9472;&#9472;&#9496;                        &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;              &#9474;
&#9474;   77<>77     81      71<>71      0        0               81<>81             &#9474;
&#9474; < Master >Master M  Headphon 3D Contr 3D Contr  3D Contr   PCM    PCM Out    &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;


I have tryed most of what i have found by googling and i am out of ideas. (thats a bit limited since i am new to kubuntu)

---

### Post by dantienn on 2007-11-09
I tryed a cuple of things before i got to bed last night with no luck. 
When i got to my computer today i started up with live cd, and the sound worked fine. I then booted up again without the live cd, and for some strange reason the sound came back. I have no idea on how and what was wrong. 
Anyway i want to thank the onlyone who replyed to my post. unclepike. Peace

---

