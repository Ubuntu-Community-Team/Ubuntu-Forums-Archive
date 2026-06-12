---
title: "No em funciona l'audio Asus M50"
date: 2009-02-17
forum: Catalan Team
---

### Post by juanal on 2009-02-17
soc un poc nou al mon de ubuntu un amic mel va aconsellar i estic provante es molt interesant pero hi ha alguns problemes amb el sistema que no he pogut solventar, he buscat per els foros i he intenta tot el que maconsellaven pero res, aquest es el meu problema sera una tonteria pero estic perdudisim:
no puc sentir res, ningun soroll del sistema, ni musica, ni pelicules, ni el soroll de amsn, ni res he instalat el alsa  o he configurat tot per a alsa pero res, no es soluciona espere que algu sapiga el que em pasa,

el meu portatil es un asus M50Cseres cpu duoP8400

gracies anticipades per la ajuda

---

### Post by papapep on 2009-02-17
Hola Juanal, benvingut al fòrum.

Abans que res, et demanaria que fessis una bona llegida a les normés de comportament a les que ens intentem acostar: [http://ubuntuforums.org/showthread.php?t=599965](http://ubuntuforums.org/showthread.php?t=599965).

Per poder mirar d'ajudar-te, caldria saber quina placa d'audio porta el teu equip (un mateix model en pot portar diferents per a diferents remeses o sub-versions).

Fes a un terminal:

```
lspci -vv
```

I enganxa el que et mostri aquí mateix, ficant-ho dins l'etiqueta CODE que surt en fer clic damunt la icona #.

També necessitem saber quina versió de nucli estàs executant. Fes:


```
uname -a
```

i enganxa el resultat.

---

### Post by juanal on 2009-02-17
> **papapep said:**
> Hola Juanal, benvingut al fòrum.

Abans que res, et demanaria que fessis una bona llegida a les normés de comportament a les que ens intentem acostar: [http://ubuntuforums.org/showthread.php?t=599965](http://ubuntuforums.org/showthread.php?t=599965).

Per poder mirar d'ajudar-te, caldria saber quina placa d'audio porta el teu equip (un mateix model en pot portar diferents per a diferents remeses o sub-versions).

Fes a un terminal:

```
lspci -vv
```

I enganxa el que et mostri aquí mateix, ficant-ho dins l'etiqueta CODE que surt en fer clic damunt la icona #.

També necessitem saber quina versió de nucli estàs executant. Fes:


```
uname -a
```

i enganxa el resultat.

```
09:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
	Subsystem: ASUSTeK Computer Inc. Device 1897
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 32 bytes
	Interrupt: pin B routed to IRQ 5
	Region 0: Memory at fdfff000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

09:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
	Subsystem: ASUSTeK Computer Inc. Device 1897
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 32 bytes
	Interrupt: pin B routed to IRQ 5
	Region 0: Memory at fdffec00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

[CODE]
```09:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
	Subsystem: ASUSTeK Computer Inc. Device 1897
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 32 bytes
	Interrupt: pin B routed to IRQ 5
	Region 0: Memory at fdfff000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

09:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
	Subsystem: ASUSTeK Computer Inc. Device 1897
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 32 bytes
	Interrupt: pin B routed to IRQ 5
	Region 0: Memory at fdffec00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

[/CODE
uname -a 
alberto@ubuntu:~$ uname -a
Linux ubuntu 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux
alberto@ubuntu:~$ 



perdo la versio de ubuntu es 8.10. gracies

---

### Post by papapep on 2009-02-17
No cal que copiis dins la teva resposta el que està en els apunts anteriors si ja està just abans. Només va bé si cal especificar a qui es respon, quan hi ha diverses persones a un mateix fil.

Crec que no has enganxat tot el que ha mostrat la ordre **lspci**. O això, o no tens ni gràfica, ni placa de xarxa, ni de wifi, ni d'audio... :-)

---

### Post by juanal on 2009-02-17
.```
[CODE]alberto@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9300M GS (rev a1)
03:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
09:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
09:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
09:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
09:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
alberto@ubuntu:~$ 


```[/CODE]
asi tens tot el que ma ixit cuan he pulsat enterinal la orde que mas dit.
al portatil tinc tambe instalat el vista i en funciona tot correctament per el que crec que si que tinc tartjeta de so de xarxa i de wifi, o no te res a vorer?

---

### Post by juanal on 2009-02-18
.```
alberto@ubuntu:~$ lspci -vv
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
	Subsystem: ASUSTeK Computer Inc. Device 1897
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: <access denied>
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: f8000000-fbffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA+ MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device 1897
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 4: I/O ports at bc00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device 1897
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 21
	Region 4: I/O ports at b880 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device 1897
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin D routed to IRQ 19
	Region 4: I/O ports at b800 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device 1897
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin C routed to IRQ 18
	Region 0: Memory at f7fffc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device 1893
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 22
	Region 0: Memory at f7ff8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
	Control: I/O- Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: fcf00000-fcffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fd000000-fddfffff
	Prefetchable memory behind bridge: 00000000f4000000-00000000f6efffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
	Control: I/O- Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
	Control: I/O- Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fde00000-fdefffff
	Prefetchable memory behind bridge: 00000000f6f00000-00000000f6ffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device 1897
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 23
	Region 4: I/O ports at b480 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device 1897
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 19
	Region 4: I/O ports at b400 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device 1897
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin C routed to IRQ 18
	Region 4: I/O ports at b080 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device 1897
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 23
	Region 0: Memory at f7fff800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01)
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=32
	Memory behind bridge: fdf00000-fdffffff
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device 1897
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: <access denied>

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) (prog-if 01)
	Subsystem: ASUSTeK Computer Inc. Device 1897
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 215
	Region 0: I/O ports at b000 [size=8]
	Region 1: I/O ports at ac00 [size=4]
	Region 2: I/O ports at a880 [size=8]
	Region 3: I/O ports at a800 [size=4]
	Region 4: I/O ports at a480 [size=32]
	Region 5: Memory at f7fff000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

01:00.0 VGA compatible controller: nVidia Corporation GeForce 9300M GS (rev a1)
	Subsystem: ASUSTeK Computer Inc. Device 19b2
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
	Region 1: Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Region 3: Memory at f8000000 (64-bit, non-prefetchable) [size=32M]
	Region 5: I/O ports at cc00 [size=128]
	[virtual] Expansion ROM at fa000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidiafb, nvidia

03:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
	Subsystem: Intel Corporation Device 1201
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 214
	Region 0: Memory at fcffe000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn

08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 16d5
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 216
	Region 0: I/O ports at e800 [size=256]
	Region 2: Memory at f6fff000 (64-bit, prefetchable) [size=4K]
	Region 4: Memory at f6fe0000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at fdef0000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

09:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 1897
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32 (500ns min, 1000ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at fdfff800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: ohci1394

09:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
	Subsystem: ASUSTeK Computer Inc. Device 1897
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 32 bytes
	Interrupt: pin B routed to IRQ 17
	Region 0: Memory at fdfff400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

09:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
	Subsystem: ASUSTeK Computer Inc. Device 1897
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 32 bytes
	Interrupt: pin B routed to IRQ 5
	Region 0: Memory at fdfff000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ricoh-mmc
	Kernel modules: ricoh_mmc

09:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
	Subsystem: ASUSTeK Computer Inc. Device 1897
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 32 bytes
	Interrupt: pin B routed to IRQ 5
	Region 0: Memory at fdffec00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

09:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff) (prog-if ff)
	!!! Unknown header type 7f

alberto@ubuntu:~$ 

```

ara siq eu ficat el comando sorrectament, en podeu ajudar?, es posible que la configuracio del sistema al instalar ubuntu cometera algun error?
el vista en funciona correctament 
gracies

---

### Post by socderafel on 2009-02-18
primer descarta totes les opcions "facils" abans de ficar-te a rebuscar drivers i configuracions. 
Mira a vore si tens tots els audios activats. on esta l'icona de l'audio (en un principi dalt a la dreta) fes doble click(o entra al mezclador) i puja totes les barres, i prova. 
A mi em passa això cada volta que faig una instal.lació en net...
si no va, ves a sistema-preferencias-sonido, i posa-ho tot en alsa.

Si açò no et funciona, ja no se que més fer... els entesos en la matèria t'ajudaran... i nosaltres continuarem l'aprenentatge...

---

### Post by juanal on 2009-02-18
ja ho he comprovat no se que estic fent mal segur que a la fi sera una tonteria ero la musica es reprodueix pero no es sent res de res o ingtente modificar en alsa i tot pero res nose que fer ja, al final segur que es una tonteria, pero mira que estic pegant-li voltes

---

### Post by socderafel on 2009-02-18
els drivers pareix que els tingues ben instal.lats, segons el que poses dalt...
has provat també que no tingues cap opció de l'audio desactivada? allò que t'he dit del mezclador¿?
a la consola, si escrius el comandament alsamixer, t'apareix un equalitzador on pots veure si els volums estan alts. es maneja amb les tecles de direcció.
un altra cosa que he llegit per ahi es:
edita l'arxiu  /etc/modprobe.d/alsa-base
i afegeix al final 

options snd-hda-intel model=3stack

reinicia i veiam si hi ha sort...

---

### Post by kukat on 2009-02-19
Salut!

Bé, a Juanal el vaig convèncer jo (el conec de tota la vida), i he estat mirant-li a veure per que no li anava el so i li vaig dir que preguntara aquí, ja que durant tota la setmana ell està a un lloc i jo a altre:p (i jo tampoc en se molt de problemes de so! jajaja)

Bé, ara pel amsn m'ha dit que va fer una insta&#320;lació amb el Wubi (Insta&#320;lant-ho des de Windows....:o)
Crec que pot ser eixe el problema ????

Ho dic per fer-li una insta&#320;lació des de zero ara que l'acaba d'insta&#320;lar. Però crec que el Wubi aquest dona problemes....

Gràcies!

---

