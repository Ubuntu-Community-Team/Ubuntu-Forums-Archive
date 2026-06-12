---
title: "Audio Problem"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by greenaged on 2007-12-22
Hi! My audio problem is that I am not getting audio through my audio card. I am getting  through the on-board audio on my MB although, I've disabled it in the BIOS.

 I have a Creative Labs Sound Blaster Live 5.1 card. My Ubuntu version is 7.10
The MB is a SOYO KT 880 Dragon 2- v2.0.

I'd be grateful for any help I can get, once it's not  technical, if that is possible. :)

Thank you
greenaged

---

### Post by as0l0 on 2007-12-23
i think the right way to change this is to go through System > *something* > sounds and then use the drop down to choose the right card.  This rarely works for me, so i have to right click on the speaker/volume icon and say preferences and do the same thing.  This also rarely works, so i have to do "asounconf list" and from there you should be able to do "asoundconf set-default-card *name*".

it's likely that i don't know what i'm doing, but i can eventually get the sound card i want.  I hope one or all of them work for you.

---

### Post by greenaged on 2007-12-24
Hi. thanks for your response. I tried your first two suggestions, but I'm afraid they didn't work.as for '"asounconf list" I don't know how to get there

---

### Post by Casual Fan on 2007-12-24
Try the steps in this thread here:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

Good luck!

---

### Post by deadgobby on 2007-12-24
You did the right thing and disable the sound card in BIOS. The next step is to get install ALSA mixer or AKA the GUI version of it. Really there is two ways around this simple task. One is to double click on the speaker icon and should bring up the mixer. Most of all the sound should be driven by the analog front sliders. So open up a MP3 file, that is if you have all the restricted formats installed. That slider is the push for it. The GUI ALSA mixer installed through Synaptic can control the same thing.  All so plug your head phones through the green out put of the card. You may want to click the option tab and bring up the Analog Front. See screen shot and go.
Gobby

---

### Post by bobpur on 2007-12-24
I have a SoundBlaster 5.1 Live X-Gamer sound card in a Compaq that dualboots WinXP and Ubuntu v7.10. 
I had the same problem with it when I first installed v6.06 in it. It had other issues that led me to re-install Ubuntu. The sound worked after that. I don't know? Maybe a file didn't install in the initial OS install. Anyhow, if all else fails...

Good Luck!

---

### Post by greenaged on 2007-12-29
Hi! I want to thank all of you who tried to help me with my audio problem, and to apologise for wasting your time. I solved the problem, quite accidentally. You see I had set up the audio system, in Windows, to play four speakers,with the headphone jack going into the SPEAKER outlet on the card, and the speaker jack into the REAR OUT outlet, for rear speakers of a receiver, so whenever I switched to Ubuntu, I didn't make, and possibly can't, get, the same set-up in Windows, and I didn't think of doing the necessary changes, hence no sound as the speaker jack was not where it should be-in the SPEAKER outlet. But today, I was messing with the sound card and I accidentally switched the headphone and speaker jacks around and, bingo, I got sound from my sound card in Ubuntu.
  I appreciate your willingness to help and for that I am very grateful.
  Once again, THANK YOU.
  greenaged :guitar:

---

### Post by frenchsquared on 2007-12-29
**** List of PLAYBACK Hardware Devices ****
card 0: MCP04 [NVidia MCP04], device 0: Intel ICH [NVidia MCP04]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: MCP04 [NVidia MCP04], device 2: Intel ICH - IEC958 [NVidia MCP04 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
gordon@Asus:~$ lspci -v
0000:00:00.0 Host bridge: nVidia Corporation: Unknown device 0071 (rev a1)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 8189
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <available only to root>

0000:00:00.1 RAM memory: nVidia Corporation: Unknown device 007f (rev a1)
        Flags: 66MHz, fast devsel

0000:00:00.2 RAM memory: nVidia Corporation: Unknown device 0075 (rev a1)
        Flags: 66MHz, fast devsel

0000:00:00.3 RAM memory: nVidia Corporation: Unknown device 006f (rev a1)
        Flags: 66MHz, fast devsel

0000:00:00.4 RAM memory: nVidia Corporation: Unknown device 00b4 (rev a1)
        Flags: bus master, 66MHz, fast devsel, latency 0

0000:00:01.0 RAM memory: nVidia Corporation: Unknown device 0076 (rev a1)
        Flags: 66MHz, fast devsel

0000:00:01.1 RAM memory: nVidia Corporation: Unknown device 0078 (rev a1)
        Flags: 66MHz, fast devsel

0000:00:01.2 RAM memory: nVidia Corporation: Unknown device 0079 (rev a1)
        Flags: 66MHz, fast devsel

0000:00:01.3 RAM memory: nVidia Corporation: Unknown device 007a (rev a1)
        Flags: 66MHz, fast devsel

0000:00:01.4 RAM memory: nVidia Corporation: Unknown device 007b (rev a1)
        Flags: 66MHz, fast devsel

0000:00:01.5 RAM memory: nVidia Corporation: Unknown device 007c (rev a1)
        Flags: 66MHz, fast devsel

0000:00:01.6 RAM memory: nVidia Corporation: Unknown device 007d (rev a1)
        Flags: 66MHz, fast devsel

0000:00:02.0 PCI bridge: nVidia Corporation: Unknown device 007e (rev a2) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: c3000000-c4ffffff
        Prefetchable memory behind bridge: 00000000b0000000-00000000bff00000
        Capabilities: <available only to root>

0000:00:09.0 RAM memory: nVidia Corporation: Unknown device 003f (rev a1)
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <available only to root>

0000:00:0a.0 ISA bridge: nVidia Corporation: Unknown device 0030 (rev a3)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 818a
        Flags: bus master, 66MHz, fast devsel, latency 0

0000:00:0a.1 SMBus: nVidia Corporation MCP04 SMBus (rev a2)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 818a
        Flags: 66MHz, fast devsel, IRQ 11
        I/O ports at e000 [size=32]
        I/O ports at 5000 [size=64]
        I/O ports at 5100 [size=64]
        Capabilities: <available only to root>

0000:00:0b.0 USB Controller: nVidia Corporation MCP04 USB Controller (rev a1) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc.: Unknown device 818a
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 209
        Memory at c5003000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:0b.1 USB Controller: nVidia Corporation MCP04 USB Controller (rev a1) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc.: Unknown device 818a
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 217
        Memory at c5004000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:0b.2 USB Controller: nVidia Corporation MCP04 USB Controller (rev a2) (prog-if 20 [EHCI])
        Subsystem: ASUSTeK Computer Inc.: Unknown device 818a
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 193
        Memory at c5000000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:00:0f.0 IDE interface: nVidia Corporation MCP04 IDE (rev f2) (prog-if 8a [Master SecP PriP])
        Subsystem: ASUSTeK Computer Inc.: Unknown device 818a
        Flags: bus master, 66MHz, fast devsel, latency 0
        I/O ports at f000 [size=16]
        Capabilities: <available only to root>

0000:00:10.0 IDE interface: nVidia Corporation MCP04 Serial ATA Controller (rev f2) (prog-if 85 [Master SecO PriO])
        Subsystem: ASUSTeK Computer Inc.: Unknown device 818a
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 193
        I/O ports at 09f0 [size=8]
        I/O ports at 0bf0 [size=4]
        I/O ports at 0970 [size=8]
        I/O ports at 0b70 [size=4]
        I/O ports at c800 [size=16]
        Memory at c5001000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:11.0 IDE interface: nVidia Corporation MCP04 Serial ATA Controller (rev f2) (prog-if 85 [Master SecO PriO])
        Subsystem: ASUSTeK Computer Inc.: Unknown device 818a
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 201
        I/O ports at 09e0 [size=8]
        I/O ports at 0be0 [size=4]
        I/O ports at 0960 [size=8]
        I/O ports at 0b60 [size=4]
        I/O ports at dc00 [size=16]
        Memory at c5002000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:12.0 PCI bridge: nVidia Corporation MCP04 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=128
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: c2000000-c2ffffff
        Prefetchable memory behind bridge: c0000000-c1ffffff

0000:00:13.0 Multimedia audio controller: nVidia Corporation MCP04 AC'97 Audio Controller (rev a1)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 812a
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 201
        I/O ports at e400 [size=256]
        I/O ports at e800 [size=256]
        Memory at c5005000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5b63 (prog-if 00 [VGA])
        Subsystem: ATI Technologies Inc: Unknown device 3000
        Flags: bus master, fast devsel, latency 0, IRQ 225
        Memory at b0000000 (32-bit, prefetchable) [size=256M]
        I/O ports at 9000 [size=256]
        Memory at c4000000 (32-bit, non-prefetchable) [size=64K]
        Expansion ROM at c3000000 [disabled] [size=128K]
        Capabilities: <available only to root>

0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 5b73
        Subsystem: ATI Technologies Inc: Unknown device 3001
        Flags: bus master, fast devsel, latency 0
        Memory at c4010000 (32-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: <available only to root>

[COLOR="Red"]0000:02:06.0 Multimedia audio controller: Creative Labs SB Audigy LS
        Subsystem: Creative Labs: Unknown device 100a
        Flags: bus master, medium devsel, latency 32, IRQ 225
        I/O ports at a000 [size=32]
        Capabilities: <available only to root>[/COLOR]

0000:02:07.0 Multimedia controller: ATI Technologies Inc: Unknown device 4d50
        Subsystem: ATI Technologies Inc: Unknown device a698
        Flags: bus master, medium devsel, latency 32, IRQ 3
        Memory at c2000000 (32-bit, non-prefetchable) [size=1M]
        Memory at c0000000 (32-bit, prefetchable) [size=32M]
        Capabilities: <available only to root>

0000:02:0c.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 80ee
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 233
        Memory at c2100000 (32-bit, non-prefetchable) [size=128K]
        I/O ports at a400 [size=64]
        Capabilities: <available only to root>

---

### Post by frenchsquared on 2007-12-29
turning off the onboard audio and reinstalling fixed it
Thanks

---

