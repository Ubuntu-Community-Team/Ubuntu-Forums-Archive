---
title: "No Sound in Feisty - Toshiba Laptop Kubuntu"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by lazyrussian on 2007-04-20
I've read probably 2 dozen threads about people who are experiencing loss of sound or sound-card support with the release of Feisty and the updated Kernel it's using.

I've tried using alsamixer, but everything there is set to zero and it won't let me increase any of the volume with my keyboard.

I've tried a Comprehensive Guide - [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) - Didn't work...

I added this code into the modeprobe.d options:
```
options snd-hda-intel model=auto
```

I'm at a loss at what I should be doing. How can I check to see if my sound-card is even detected?

---

### Post by silverglade00 on 2007-04-20
Try model=test. That's supposed to be a minimal base config.

---

### Post by celsdogg on 2007-04-20
im having trouble too, but it is with audio skipping. i hear the login sound for an hour before it ends. i shoulda stuck with edgy for awhile.

i am also using a toshiba laptop, a A25-S279.

---

### Post by lazyrussian on 2007-04-20
Didn't work. I think my sound card hardware isn't recognized.
How can I check for this?

---

### Post by macogw on 2007-04-20
```
lspci -vv
```
what's that tell ya?  does it give a name for the sound card or "unknown device"?

---

### Post by lazyrussian on 2007-04-20
Here's the output
```

00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
        Latency: 64

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: d0000000-d00fffff
        Prefetchable memory behind bridge: d8000000-dfffffff
        Secondary status: 66MHz+ FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA+ VGA+ MAbort- >Reset- FastB2B-
        Capabilities: <access denied>

00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 32 bytes
        Bus: primary=00, secondary=02, subordinate=04, sec-latency=0
        Memory behind bridge: d0100000-d01fffff
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
        Capabilities: <access denied>

00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
        Control: I/O- Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 32 bytes
        Bus: primary=00, secondary=05, subordinate=07, sec-latency=0
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
        Capabilities: <access denied>

00:07.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
        Control: I/O- Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 32 bytes
        Bus: primary=00, secondary=08, subordinate=0a, sec-latency=0
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
        Capabilities: <access denied>

00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64, Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 17
        Region 0: I/O ports at 8440 [size=8]
        Region 1: I/O ports at 8430 [size=4]
        Region 2: I/O ports at 8420 [size=8]
        Region 3: I/O ports at 8410 [size=4]
        Region 4: I/O ports at 8400 [size=16]
        Region 5: Memory at d0507000 (32-bit, non-prefetchable) [size=512]
        [virtual] Expansion ROM at 24000000 [disabled] [size=512K]
        Capabilities: <access denied>

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64, Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 18
        Region 0: Memory at d0504000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64, Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 18
        Region 0: Memory at d0505000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80) (prog-if 20 [EHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64, Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 18
        Region 0: Memory at d0506000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Region 0: I/O ports at 8450 [size=16]
        Region 1: Memory at d0507400 (32-bit, non-prefetchable) [size=1K]

00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80) (prog-if 8a [Master SecP PriP])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 19
        Region 0: I/O ports at 01f0 [size=8]
        Region 1: I/O ports at 03f4 [size=1]
        Region 2: I/O ports at 0170 [size=8]
        Region 3: I/O ports at 0374 [size=1]
        Region 4: I/O ports at 8460 [size=16]
        Capabilities: <access denied>

00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64, Cache Line Size: 32 bytes
        Interrupt: pin ? routed to IRQ 19
        Region 0: Memory at d0500000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
        Subsystem: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
        Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80) (prog-if 01 [Subtractive decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64
        Bus: primary=00, secondary=0b, subordinate=0d, sec-latency=64
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: d0200000-d02fffff
        Prefetchable memory behind bridge: 20000000-23ffffff
        Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
        BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-

01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M] (prog-if 00 [VGA])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 255 (2000ns min), Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 22
        Region 0: Memory at d8000000 (32-bit, prefetchable) [size=128M]
        Region 1: I/O ports at 9000 [size=256]
        Region 2: Memory at d0000000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at d0020000 [disabled] [size=128K]
        Capabilities: <access denied>

02:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
        Subsystem: Askey Computer Corp. Unknown device 7106
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 19
        Region 0: Memory at d0100000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

0b:06.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 168, Cache Line Size: 128 bytes
        Interrupt: pin A routed to IRQ 16
        Region 0: Memory at febfe000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=0b, secondary=0c, subordinate=0c, sec-latency=176
        Memory window 0: 20000000-23fff000 (prefetchable)
        Memory window 1: 28000000-2bfff000
        I/O window 0: 0000a800-0000a8ff
        I/O window 1: 0000ac00-0000acff
        BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset+ 16bInt+ PostWrite+
        16-bit legacy interface ports at 0001

0b:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (8000ns min, 16000ns max)
        Interrupt: pin A routed to IRQ 20
        Region 0: I/O ports at a000 [size=256]
        Region 1: Memory at d0200800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

0b:0a.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0) (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (8000ns max), Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 17
        Region 0: Memory at d0200000 (32-bit, non-prefetchable) [size=2K]
        Region 1: I/O ports at a400 [size=128]
        Capabilities: <access denied>

```

---

### Post by lazyrussian on 2007-04-20
I think this is it:

```

Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64, Cache Line Size: 32 bytes
        Interrupt: pin ? routed to IRQ 19
        Region 0: Memory at d0500000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

```

---

### Post by perldog007 on 2007-04-20
That is similar to what I have:

00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64, Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 11
        Region 0: Memory at b0000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>


I had to d/l and build the realtek linuxpack 4.05f (amd 64 on Acer Aspire craptop)  for edgy, now it just won't work and rebuilding has thus far proven fruitless, gonna try it again and play closer attn to errors in ./install.....:guitar:

---

### Post by perldog007 on 2007-04-20
Ok,

  here is what I got when I ran the install script that came with the realtek-linuxpack-4.05f which worked well with the last update in Edgy.

  Apparently these folks are determined to make VISTA look good in the backward compatibility compartment.  I will take a shot at this, but honestly it is way over my head. Any help would be much appreciated. would re-install edgy b4 I boot winblows just to have sound.

---

### Post by seesixty on 2007-04-20
I have the same problem with a Toshiba Satellite A100,
```

~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

~$ lspci -vv
 00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64, Cache Line Size: 32 bytes
        Interrupt: pin ? routed to IRQ 19
        Region 0: Memory at c0500000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

~$ cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xc0500000 irq 19
```

I think [_this bug #106296_]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106296") is the problem, but can't seem to work past it.

---

### Post by perldog007 on 2007-04-20
THanks for that. My kindegarten level and pre wireless era C skills were no match for that.  Guess we stand by until they fix it. I am out of ideas unless realtek releases an updated driver.

---

### Post by lazyrussian on 2007-04-20
I just spent an hour looking through possible solutions on launchpad and all other posts in the forums - This problem isn't going away anytime soon

I'm going back to edgy until Gutsy comes out in October.

---

### Post by perldog007 on 2007-04-21
OK,

  I got sound through the headphone jack and no capture with a little RTFM @ [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

    seems that the proprietary realtek drivers that work with my laptop (Acer Aspire 3131) will not work with the new kernel/libs I really can't make the distinction. The hda-intel driver in alsa only gives me partial sound. 

  GUess that means I wait until realtek releases an updated driver...... anywho the instructions in the link above will prolly help alot of folk. Just remember to check version numbers, if you cut and paste the code on the post it will break in feisty.  

    I.E. if you cut and paste the wget for alsa driver source it will grab an older version, instead use your browser to hit the [ftp://....../pub/drivers](ftp://....../pub/drivers) and get the latest one for feisty.

:guitar:

---

### Post by perldog007 on 2007-04-22
Okay Kids,

  I just pwn3d mine own self.  Despite using linux since slackware 2.0.....

   The realtek drivers (linux audio pack found here: [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=23&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=23&Level=4&Conn=3&DownTypeID=3&GetDown=false))
are GPL.

   Despite having the big boys warranty ( ALA MMURLT, you have the code fix it yourself) I just assumed that it was proprietary.

   The problem with feisty seems to be that the latest version 1.0.12-4.05f or some such won't compile under feisty, looking at the errors it looks lifke lib updates, but I haven't cut any C since '97 
so it could just be senility on my part. 

  From what I can glean, the realtek implementation of the hda-intel chipset has some subtle differences that warrants realtek putting out their own driver packs. 4.05f is date two months ago and prolly wont work in the latest kernel. 

  Here is how I got stereo through the headphone Jack.

   Get audio pack above.

   tar xjvf the .bz2 file and cd into that directory.

   rm the driver, lib, and util compressed tarballs.

   download the 1.0.14rc2 drivers from [ftp://ftp.alsa-project.org/pub/](ftp://ftp.alsa-project.org/pub/)

  change the install script to use the 1.0.14*xxx* files.

  at the shell prompt run : sudo ./install

  Today I will sentence mine own dumb @$$ to looking at the realtek code in *xx[I][I]-4[I].05f*[/I][/I][/I] [I]and comparing it to the "regular" alsa driver code. But since I never wrote or maintained any driver code, or any C code for the last decade I am betting that somebody beats me to it. 

   Moral of the story, if you are running feisty with the realtek hda-intel chipset in your soundcard, keep your eye on the realtek driver downloads page. in the meantime use the alsa 
1.0.13 or better drivers, lib and utils. 
TO BE CONTINUED.

---

### Post by mindcrusher on 2007-04-22
> **seesixty said:**
> I have the same problem with a Toshiba Satellite A100,
```

~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

~$ lspci -vv
 00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64, Cache Line Size: 32 bytes
        Interrupt: pin ? routed to IRQ 19
        Region 0: Memory at c0500000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

~$ cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xc0500000 irq 19
```

I think [_this bug #106296_]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106296") is the problem, but can't seem to work past it.

My Toshiba Satelltie A105-S2051 gives the same outputs and none of the fixes on this forum worked for me.
I also have the USB handoff problem where the USB mouse would simply die after a time.

It's strange that both the mouse and sound worked fine under Kubuntu 6.04, then mouse broke (USB issue) in Kubuntu 6.10, and now in Ubuntu 7.04 they are both a problem.

---

### Post by dustman on 2007-04-23
yo...mindcrusher...about the mouse issue...I also had it ( I have a Toshiba A100-529 ), but solved it by adding "noapic irqpoll" as boot options to the kernel. Hope it works!


Cheers!

Radu

P.S. I have the same sound problem like most of the people that upgraded to feisty :(. The output of "**lspci -vv**"  , "**aplay -l**" and  "**cat /proc/asound/cards**" are the same(or at least similar) like at all you guys...still haven't found the solution :|

---

### Post by djails on 2007-04-23
Have a look at my post about SB450 in toshiba laptops for a solution and let me know if it does the job.
[http://ubuntuforums.org/showthread.php?p=2515443#post2515443](http://ubuntuforums.org/showthread.php?p=2515443#post2515443)

---

### Post by dustman on 2007-04-23
> **djails said:**
> Have a look at my post about SB450 in toshiba laptops for a solution and let me know if it does the job.
[http://ubuntuforums.org/showthread.php?p=2515443#post2515443](http://ubuntuforums.org/showthread.php?p=2515443#post2515443)


man, I get that the device is busy...:
```
ERROR: Module snd_hda_intel is in use
```
Perhaps I have to boot into recovery mode, and then issue those commands....:D

---

### Post by lazyrussian on 2007-04-23
I get the same message :(

---

### Post by b4silence on 2007-04-26
try it in recover mode and you'll get it... :popcorn:

---

