---
title: "No sound"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by Partyboi2 on 2007-01-11
[FONT="Comic Sans MS"][/FONT]


I am a compete newbie to linux and have installed ubuntu 6.06, but I have no sound. The sound card is a ES 1869 Plug PnP, Where can I get the drivers for it to work? Also how do I install the drivers? Any help would be appreciated. 
Thanks
:confused:

---

### Post by azkehmm on 2007-01-11
Is it a sorround system? If so, you might want to open you Alsamixer through the terminal and try and unmute Master sorround and "Flood speakers to front" (i think it's called) that helped me a huge bit with my sorround system.

---

### Post by energiya on 2007-01-11
> **azkehmm said:**
> Is it a sorround system? If so, you might want to open you Alsamixer through the terminal and try and unmute Master sorround and "Flood speakers to front" (i think it's called) that helped me a huge bit with my sorround system.

open a terminal, and write
```
alsamixer
```
Master and PCM shouldn't  have "MM". If one of them has "MM" and not "00" select it and pres the "m" key. Use Up/Down arrow to increase/lower the volume. Also, enable any other you might need, as azkehmm said.

---

### Post by Ben Sprinkle on 2007-01-11
Mabey you don't have installed?
```

sudo apt-get install gnome-audio

```
I would think ubu has it though.

---

### Post by Partyboi2 on 2007-01-11
I tried  sudo apt-get install gnome-audio   and this is what I get:

Reading package lists... Done
Building dependency tree... Done
Package gnome-audio is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gnome-audio has no installation candidate

I have no idea what this means or what to do lol

---

### Post by Pixilarion on 2007-01-11
Is this card supported by the kernel?

Try this:
```

sudo modprobe snd-es18xx

```

After that you should try to play some sound...

---

### Post by Partyboi2 on 2007-01-12
I tried sudo modprobe snd-esl 8xx and got:

FATAL: Error inserting snd_es18xx (/lib/modules/2.6.15-27-386/kernel/sound/isa/snd-es18xx.ko): No such device

Does this mean I am gonna have to get another sound card? Or is there a way around this?

:mrgreen:

---

### Post by ComplexNumber on 2007-01-12
> **Partyboi2 said:**
> I tried sudo modprobe snd-esl 8xx and got:

FATAL: Error inserting snd_es18xx (/lib/modules/2.6.15-27-386/kernel/sound/isa/snd-es18xx.ko): No such device

Does this mean I am gonna have to get another sound card? Or is there a way around this?

:mrgreen:
have a look at [this]("http://ubuntuforums.org/showthread.php?t=205449").

---

### Post by Partyboi2 on 2007-01-14
Ok I tried following the instructions/how to on this page [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

I tried getting drivers from a *fresh* kernel but that didnt work.
I tried ALSA driver Compilation butl it says: Package `alsa-source' is not installed and no info is available. 
Am I doing something wrong? 

This is what I have done so far: (I have a Es1869 plugnplay)  (snd-es18xx)

karl@karl-desktop:~$ aplay -l
aplay: device_list:221: no soundcards found...
karl@karl-desktop:~$ lspci -v
0000:00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
        Flags: bus master, medium devsel, latency 64
        Memory at 44000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <available only to root>

0000:00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 00001000-00001fff
        Memory behind bridge: 40000000-410fffff
        Prefetchable memory behind bridge: 20000000-200fffff

0000:00:0d.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 08)
        Subsystem: Intel Corporation EtherExpress PRO/100+ Management Adapter with Alert On LAN*
        Flags: bus master, medium devsel, latency 66, IRQ 11
        Memory at 41200000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 2000 [size=64]
        Memory at 41100000 (32-bit, non-prefetchable) [size=1M]
        Expansion ROM at 20100000 [disabled] [size=1M]
        Capabilities: <available only to root>

0000:00:14.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
        Flags: bus master, medium devsel, latency 0

0000:00:14.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])
        Flags: bus master, medium devsel, latency 64
        I/O ports at 2060 [size=16]

0000:00:14.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01) (prog-if 00 [UHCI])
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at 2040 [size=32]

0000:00:14.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
        Flags: medium devsel, IRQ 9

0000:01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c) (prog-if 00 [VGA])
        Subsystem: ATI Technologies Inc Rage Pro Turbo AGP 2X
        Flags: bus master, stepping, medium devsel, latency 66, IRQ 11
        Memory at 40000000 (32-bit, non-prefetchable) [size=16M]
        I/O ports at 1000 [size=256]
        Memory at 41000000 (32-bit, non-prefetchable) [size=4K]
        Expansion ROM at 20000000 [disabled] [size=128K]
        Capabilities: <available only to root>

karl@karl-desktop:~$ sudo modprobe snd-
Display all 134 possibilities? (y or n)
snd-ac97-bus        snd-ens1370         snd-pcm-oss
snd-ac97-codec      snd-ens1371         snd-pdaudiocf
snd-ad1816a         snd-es1688          snd-rawmidi
snd-ad1816a-lib     snd-es1688-lib      snd-rme32
snd-ad1848          snd-es18xx          snd-rme96
snd-ad1848-lib      snd-es1938          snd-rme9652
snd-ad1889          snd-es1968          snd-rtctimer
snd-ainstr-fm       snd-es968           snd-sb16
snd-ainstr-gf1      snd-fm801           snd-sb16-csp
snd-ainstr-iw       snd-gusclassic      snd-sb16-dsp
snd-ainstr-simple   snd-gusextreme      snd-sb8
snd-ak4114          snd-gus-lib         snd-sb8-dsp
snd-ak4117          snd-gusmax          snd-sbawe
snd-ak4531-codec    snd-gus-synth       snd-sb-common
snd-ak4xxx-adda     snd-hda-codec       snd-seq
snd-ali5451         snd-hda-intel       snd-seq-device
snd-als100          snd-hdsp            snd-seq-dummy
snd-als4000         snd-hdspm           snd-seq-instr
snd-atiixp          snd-hwdep           snd-seq-midi
snd-atiixp-modem    snd-i2c             snd-seq-midi-emul
snd-au8810          snd-ice1712         snd-seq-midi-event
snd-au8820          snd-ice1724         snd-seq-oss
snd-au8830          snd-ice17xx-ak4xxx  snd-seq-virmidi
snd-azt2320         snd-intel8x0        snd-serial-u16550
snd-azt3328         snd-intel8x0m       snd-sgalaxy
snd-bt87x           snd-interwave       snd-sonicvibes
snd-bt-sco          snd-interwave-stb   snd-sscape
snd-ca0106          snd-korg1212        snd-tea575x-tuner
snd-cmi8330         snd-maestro3        snd-tea6330t
snd-cmipci          snd-mixart          snd-timer
snd-cs4231          snd-mixer-oss       snd-trident
snd-cs4231-lib      snd-mpu401          snd-trident-synth
snd-cs4232          snd-mpu401-uart     snd-usb-audio
snd-cs4236          snd-mtpav           snd-usb-lib
snd-cs4236-lib      snd-nm256           snd-usb-usx2y
snd-cs4281          snd-opl3-lib        snd-util-mem
snd-cs46xx          snd-opl3sa2         snd-via82xx
snd-cs8427          snd-opl3-synth      snd-via82xx-modem
snd-dt019x          snd-opl4-lib        snd-virmidi
snd-dummy           snd-opl4-synth      snd-vx222
snd-emu10k1         snd-opti92x-ad1848  snd-vx-lib
snd-emu10k1-synth   snd-opti92x-cs4231  snd-vxpocket
snd-emu10k1x        snd-opti93x         snd-wavefront
snd-emu8000-synth   snd-page-alloc      snd-ymfpci
snd-emux-synth      snd-pcm
karl@karl-desktop:~$ sudo modprobe snd-es18xx
Password:
FATAL: Error inserting snd_es18xx (/lib/modules/2.6.15-27-386/kernel/sound/isa/snd-es18xx.ko): No such device
karl@karl-desktop:~$ modinfo soundcore
filename:       /lib/modules/2.6.15-27-386/kernel/sound/soundcore.ko
description:    Core sound module
author:         Alan Cox
license:        GPL
alias:          char-major-14-*
vermagic:       2.6.15-27-386 preempt 486 gcc-4.0
depends:
srcversion:     DD426F1CCA2CC5F060F6F92
karl@karl-desktop:~$ sudo apt-get install build-essential linux-headers-$(uname -r) module-assistant alsa-source
Password:
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
linux-headers-2.6.15-27-386 is already the newest version.
E: Couldn't find package module-assistant
karl@karl-desktop:~$ sudo dpkg-reconfigure alsa-source
Package `alsa-source' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: alsa-source is not installed
karl@karl-desktop:~$

---

### Post by Ben Sprinkle on 2007-01-14
```

sudo apt-get install alsa-source

```
Try that.
Or:
```

sudp apt-source alsa-source

```
I think.

---

### Post by Partyboi2 on 2007-01-16
After going through all the info that u people have passed on to me and mangaging to get my head around it all, I was able to get sound!!!! Now just need to tweak it.
Thank u all for ur help.

:D  :D  :D

---

### Post by Ben Sprinkle on 2007-01-16
:)

---

