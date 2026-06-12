---
title: "yet another no sound help request thread (mainly concerned with tascam us-428)"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by cingo on 2008-01-26
Hallo,
I have been using ubuntu for a while now and never got round to get it to play any sound.
I have been through a good number of help tutorials (from these forums), installed and removed stuff, and nothing works. I have a nvidia sound card and a glorious old tascam us-428 that I would love to get up and running (more than happy to forget about the nvidia)

My last step was a purge and a clean install of alsa, when I try to run alsamixer (whatever it is, it is one of the things I am requested to do in the tutorials).

alsamixer: relocation error: alsamixer: symbol snd_mixer_selem_get_playback_dB, version ALSA_0.9 not defined in file libasound.so.2 with link time reference

Please help... I waisted whole days on this and nothing works.
Many thanks.

---

### Post by cingo on 2008-01-26
oh and I am also told

**** List of PLAYBACK Hardware Devices ****
card 1: snd_ctl_card_info_get_id [Nvidia CK8S], device 0: OSS ID [Nvidia CK8S]
  Subdevices: 1/1
  Subdevice #0: OSS subname
card 1: snd_ctl_card_info_get_id [Nvidia CK8S], device 1: OSS ID [Nvidia CK8S S/PDIF out]
  Subdevices: 1/1
  Subdevice #0: OSS subname
cingo@cingo-desktop:~$ alsamixer


********************   WARNING   *******************************
Warning! alsamixer uses ALSA emulation instead of the native OSS API
****************************************************************

snd_mixer_set_callback()




last but not least, let me tell you that (just in case someone asks)



cingo@cingo-desktop:~$ lspci -v
00:00.0 Host bridge: nVidia Corporation nForce3 250Gb Host Bridge (rev a1)
        Flags: bus master, 66MHz, fast devsel, latency 0
        Memory at f6000000 (32-bit, prefetchable) [size=32M]
        Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation nForce3 250Gb LPC Bridge (rev a2)
        Subsystem: Giga-byte Technology Unknown device 0c11
        Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation nForce 250Gb PCI System Management (rev a1)
        Subsystem: Giga-byte Technology Unknown device 0c11
        Flags: 66MHz, fast devsel, IRQ 10
        I/O ports at e400 [size=32]
        I/O ports at 1c00 [size=64]
        I/O ports at 2000 [size=64]
        Capabilities: <access denied>

00:02.0 USB Controller: nVidia Corporation CK8S USB Controller (rev a1) (prog-if 10 [OHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
        Memory at fd003000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:02.1 USB Controller: nVidia Corporation CK8S USB Controller (rev a1) (prog-if 10 [OHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
        Memory at fd004000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:02.2 USB Controller: nVidia Corporation nForce3 EHCI USB 2.0 Controller (rev a2) (prog-if 20 [EHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
        Memory at fd005000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:05.0 Bridge: nVidia Corporation CK8S Ethernet Controller (rev a2)
        Subsystem: Giga-byte Technology Unknown device e000
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
        Memory at fd000000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at b800 [size=8]
        Capabilities: <access denied>

00:06.0 Multimedia audio controller: nVidia Corporation nForce3 250Gb AC'97 Audio Controller (rev a1)
        Subsystem: Giga-byte Technology Unknown device a002
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
        I/O ports at bc00 [size=256]
        I/O ports at c000 [size=128]
        Memory at fd001000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:08.0 IDE interface: nVidia Corporation CK8S Parallel ATA Controller (v2.5) (rev a2) (prog-if 8a [Master SecP PriP])
        Subsystem: Giga-byte Technology Unknown device 5002
        Flags: bus master, 66MHz, fast devsel, latency 0
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at f000 [size=16]
        Capabilities: <access denied>

00:0a.0 IDE interface: nVidia Corporation CK8S Serial ATA Controller (v2.5) (rev a2) (prog-if 85 [Master SecO PriO])
        Subsystem: Giga-byte Technology Unknown device b002
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
        I/O ports at 09f0 [size=8]
        I/O ports at 0bf0 [size=4]
        I/O ports at 0970 [size=8]
        I/O ports at 0b70 [size=4]
        I/O ports at dc00 [size=16]
        I/O ports at e000 [size=128]
        Capabilities: <access denied>

00:0b.0 PCI bridge: nVidia Corporation nForce3 250Gb AGP Host to PCI Bridge (rev a2) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 16
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=10
        Memory behind bridge: fa000000-fbffffff
        Prefetchable memory behind bridge: f8000000-f9ffffff

00:0e.0 PCI bridge: nVidia Corporation nForce3 250Gb PCI-to-PCI Bridge (rev a2) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=128
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: fc000000-fcffffff

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel

01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15) (prog-if 00 [VGA])
        Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 16
        Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
        Memory at f8000000 (32-bit, prefetchable) [size=32M]
        [virtual] Expansion ROM at fb000000 [disabled] [size=64K]
        Capabilities: <access denied>

02:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46) (prog-if 10 [OHCI])
        Subsystem: VIA Technologies, Inc. IEEE 1394 Host Controller
        Flags: bus master, stepping, medium devsel, latency 32, IRQ 16
        Memory at fc000000 (32-bit, non-prefetchable) [size=2K]
        I/O ports at a000 [size=128]
        Capabilities: <access denied>

---

### Post by cingo on 2008-01-26
Could an admin please move this thread to
Main Support Categories  > Multimedia & Video
I suspect it would be more suited for that category and apologize for the wrong choice

---

### Post by cingo on 2008-01-27
well, if someone would at least hint at how to get my nvidia to play sound I would already be very grateful :)

---

### Post by cingo on 2008-01-27
I installed ubuntu studio, which got me an alsa mixer and some gadgets.
All pretty useless though, as I still have no sound on the nvdia and no life on the us-428.
Shall I just install vista and give up?

---

### Post by philinux on 2008-01-27
Post your full system specs. It might help.

---

### Post by cingo on 2008-01-27
are they not all in the long list above?

os is ubuntu 7.10 + all the ubuntu studio I could get

---

### Post by cingo on 2008-02-03
Here is an update (for the future generations I guess).
Ubuntu studio helps: it did fix some things.
Getting a sound blaster live also helps.
And reinstalling alsa completely helps too.
Restarting a couple of times after that is not bad.

As for the us-428, I am not done yet. But the usual procedure for the us-122 works, provided you modify the text file you have to save with gedit: change us-122 to us-428 (one instance), 8006 to 8000 and 8007 to 8001.
After a couple more reboots I got the green light.
This does not mean it is working, but at least computer and tascam acknowledge each other's presence.

More later, hopefully.
(help still welcome!)

---

### Post by rrosajrj on 2008-02-17
I've wasted a few hours on trying to get my 428 installed, too.  I've gotten nowhere.  I changed from ubuntu to ubuntu studio and it runs pretty good, but I can't make the 428 do anything at all.  I'm about ready to forget about it and just use the vista software...

Let me know if you ever figure anything out though.  Thanks-

---

### Post by cingo on 2008-02-18
Same for me, the old us-428 is absolutely useless at the moment.
It looks like either noone has managed to fix it, or noone has seen this thread (or noone can be bothered to answer).
Too bad, I liked my us-428 until I could do something with it. Now it is just collecting dust.

---

### Post by jazzman on 2008-07-11
Try this link. It should work.

[http://alsa.opensrc.org/index.php/Tascam_US-428](http://alsa.opensrc.org/index.php/Tascam_US-428)

---

