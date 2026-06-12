---
title: "MacMini + 8.10 = no sound when headphones connected?"
date: 2009-01-17
forum: Apple Hardware Users
---

### Post by jiragh on 2009-01-17
Hi,

I just tried the Ubuntu 8.10 live cd on my Intel based MacMini. Basic usage looks fine except for the fact, that sound only works, if nothing is plugged in the headphone connector. *Huhhh* ?? As I use the MacMini as some kind of "media server", it is connected to my hi-fi system (at least when running on Mac OS X).
Any hints on how to get sound working *with* the audio cable *connected* to the headphone port?

Here is the "lspci -vvv" output, if that helps:

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Subsystem: SigmaTel Device 7680
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 256 bytes
	Interrupt: pin A routed to IRQ 22
	Region 0: Memory at 90440000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

Thanks for any help!

edit: It is a MacMini2,1 (Intel Core 2 Duo 1,83 GHz)

---

### Post by jiragh on 2009-01-17
Hmm, the problem (somehow) solved itself: I booted into Mac OS X again, turned the OS X sound level up from 75% to 100% booted into Ubuntu live, set the Ubuntu (master) sound level from 75% to 100% and also the headphone sound level from 75% to 100%. Now sound "arrives" at the speakers of my hi-fi :)

---

### Post by McFrostey on 2009-01-18
Applications>Accesories>Terminal

"sudo modprobe snd-powermac"

right click the speaker icon at the top of the screen on the toolbar and click volume control, there ya go.

---

### Post by cyberdork33 on 2009-01-18
> **McFrostey said:**
> Applications>Accesories>Terminal

"sudo modprobe snd-powermac"

right click the speaker icon at the top of the screen on the toolbar and click volume control, there ya go.
He has an Intel Mac Mini... that is a driver for the PPC Mac Mini.

---

