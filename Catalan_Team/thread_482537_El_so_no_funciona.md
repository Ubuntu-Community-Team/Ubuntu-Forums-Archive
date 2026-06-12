---
title: "El so no funciona"
date: 2007-06-23
forum: Catalan Team
---

### Post by utep on 2007-06-23
A vegades funciona i a vegades no... amb res (ni cds ni webs ni videos nio res de res...
Ara però fa uns dies que no em funciona... ja he consultat alguns foros amb problemes similars però despres de provar algunes coses sense èxit he decidit, tornar-vos a molestar...

A vere, tinc per una banda això:

[IMG]http://img526.imageshack.us/img526/5623/capturapm2.png[/IMG]

Per una altra banda desde teminal he posat "alsamixer" i he pujat el volum de tot el que he pogut.

També enganxo la sortida d'algunes ordres que he fet desde el terminal abans de que m'ho demaneu:

> aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SI7012 [SiS SI7012], device 0: Intel ICH [SiS SI7012]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Live [SB Live 5.1 [SB0220]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 1: Live [SB Live 5.1 [SB0220]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: Live [SB Live 5.1 [SB0220]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


> lspci -v
00:00.0 Host bridge: Silicon Integrated Systems [SiS] SiS645DX Host & Memory & AGP Controller (rev 01)
        Subsystem: ASUSTeK Computer Inc. Unknown device 8081
        Flags: bus master, medium devsel, latency 32
        Memory at e8000000 (32-bit, non-prefetchable) [size=64M]
        Capabilities: <access denied>

00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: e7000000-e7ffffff
        Prefetchable memory behind bridge: eff00000-febfffff

00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 25)
        Flags: bus master, medium devsel, latency 0

00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
        Flags: medium devsel
        I/O ports at e600 [size=32]

00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (prog-if 80 [Master])
        Subsystem: ASUSTeK Computer Inc. Unknown device 807a
        Flags: bus master, medium devsel, latency 128, IRQ 19
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at b400 [size=16]

00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
        Subsystem: ASUSTeK Computer Inc. Unknown device 80b0
        Flags: bus master, medium devsel, latency 32, IRQ 21
        I/O ports at a400 [size=256]
        I/O ports at a000 [size=128]
        Capabilities: <access denied>

00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 807a
        Flags: bus master, medium devsel, latency 32, IRQ 20
        Memory at e6800000 (32-bit, non-prefetchable) [size=4K]

00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 807a
        Flags: bus master, medium devsel, latency 32, IRQ 16
        Memory at e6000000 (32-bit, non-prefetchable) [size=4K]

00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller (prog-if 20 [EHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 807a
        Flags: bus master, medium devsel, latency 32, IRQ 17
        Memory at e5800000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
        Subsystem: ASUSTeK Computer Inc. Unknown device 80a7
        Flags: bus master, medium devsel, latency 32, IRQ 18
        I/O ports at 9800 [size=256]
        Memory at e5000000 (32-bit, non-prefetchable) [size=4K]
        Expansion ROM at efee0000 [disabled] [size=128K]
        Capabilities: <access denied>

00:0f.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
        Subsystem: Creative Labs SBLive! 5.1 Digital Model SB0220
        Flags: bus master, medium devsel, latency 32, IRQ 21
        I/O ports at 9400 [size=32]
        Capabilities: <access denied>

00:0f.1 Input device controller: Creative Labs SB Live! Game Port (rev 0a)
        Subsystem: Creative Labs Gameport Joystick
        Flags: bus master, medium devsel, latency 32
        I/O ports at 9000 [size=8]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2) (prog-if 00 [VGA])
        Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 19
        Memory at e7000000 (32-bit, non-prefetchable) [size=16M]
        Memory at f0000000 (32-bit, prefetchable) [size=128M]
        [virtual] Expansion ROM at efff0000 [disabled] [size=64K]
        Capabilities: <access denied>


Gràcies per anticipat!
utep

---

### Post by prostata on 2007-06-24
aquest és un problema "estable" ;-) d'ubuntu, a mi també  m'ho fa de tant en tant i la sol-lució és la següenta, clica sobre l'icono del só a dalt a a la dreta, dos cops, quan s'obri fixat en que tot estigui "desmarcat" però sobre tot allà on diu PCM. Si apareix marcat el desmarques i això arregla temporalment el problema....

salut

---

### Post by utep on 2007-06-25
Merci! ho posaré en pràctica... tot i així tb he observat que a vegades el so funciona amb l'opció PCM marcada... pero bueno...
 Merci!
utep

---

### Post by lluisanunez on 2007-06-30
Potser et passa perquè tens "Detecta automàticament" a Sistema >> Preferencies >> So i de vegades et detecta un driver i de vegades un altre?

---

### Post by papapep on 2007-11-08
Benvingut al fòrum Jutipiris, 

Si us plau, fes un cop d'ull al post que hi ha destacat al principi del fòrum [http://ubuntuforums.org/showthread.php?t=599965](http://ubuntuforums.org/showthread.php?t=599965) ja que si no vigilem una mica en com fem anar els fils i com formulem les preguntes tots plegats perdem un munt de temps que podríem dedicar a esbrinar el problema real:

* Cal que expliquis quina versió i variant d'Ubuntu fas servir.
* Cal que deixis clar quina placa de so tens, i si en tens alguna altra al sistema o no (hi ha gent que en té una a la placa mare i una de pci)

Quanta més informació ens donguis més podem afinar la resposta al teu problema.

Per cert, no és una bona idea agafar un fil de fa quatre mesos i reviure'l, quan no és la mateixa placa de so la que porta el problema. Encara que tot vagi de so, poden ser problemes radicalment diferents.
Moc tots els posts nous a un fil nou (excepte aquest) per a poder-ho tractar com cal.

Aquí teniu el nou fil: [http://ubuntuforums.org/showthread.php?t=607004](http://ubuntuforums.org/showthread.php?t=607004)

---

