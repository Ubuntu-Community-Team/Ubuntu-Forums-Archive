---
title: "Phase88 Rack PCI dissapears after shutdown"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by SoundMind on 2008-01-14
Alright, I was raised using DOS, moved through WinXP. All things Linux are Greek to me so Please be patient.

Here's the rundown:

I installed Ubuntu Studio (7.10) less than a week ago. Everything worked on the first successful install (device wise, anyway). After a while, my Terratec Producer Phase88 Rack PCI stopped working. I did rather a lot of googling and reading posts here and elsewhere I found very little aside from the [COLOR="Red"]"[Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449&highlight=ice1712")"[/COLOR]. The card shows up as the primary (and only, as the onboard is disabled in the BIOS) sound device when using ```
aplay -l
```as follows: ```
card 0: Phase88 [TerraTec Phase88], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Phase88 [TerraTec Phase88], device 1: ICE1712 consumer [ICE1712 consumer]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Phase88 [TerraTec Phase88], device 2: ICE1712 consumer (DS) [ICE1712 consumer (DS)]
  Subdevices: 6/6
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
```

After a shutdown and restart, the card is gone (judging by said same command).

On to step 2 and 
```
lspci -v
```

Which yeilds a list of all things PCI and some things not. The important thing is it shows only one soundcard:```
01:07.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
        Subsystem: TERRATEC Electronic GmbH PHASE88
        Flags: bus master, medium devsel, latency 64, IRQ 20
        I/O ports at cc00 [size=32]
        I/O ports at c880 [size=16]
        I/O ports at c800 [size=16]
        I/O ports at c480 [size=64]
        Capabilities: <access denied>
```

When working there are 12 devices under the ICE1712 [ENVY24] heading. When it is not, there's just the [COLOR="Red"]"ICE1712 [ENVY24] PCI Multi-Channel I/O Controller"[/COLOR]. What kills me is that it is still properly identified as a Terratec Phase88, but in the  [COLOR="Red"]"Sound Preferences"[/COLOR] dialog and via the aplay-l command, it doesn't exist.


Under both working and non-working conditions, no modules are loaded. From what I have read, I gathered that the drivers are complied into the kernel(?). After all of this I tried the procedure under [COLOR="Red"]"Getting the ALSA drivers from a *fresh* kernel"[/COLOR] in the sound solutions guide. This tends to work.., Not every time, but most of the time it will restore sound for the session after a shutdown and restart. After that, a shutdown and restart yeilds... no more Phase88.


Have you soaked all that in, gentle reader? Now here's the rub. I mean the really unique thing. If I shut down and power back on, my soundcard is stil gone. If I power up and then hit restart, I have sound. I have tried this several times and it worked every time. No dump and reload of the ALSA drivers or anything else; just hitting the restart button in my shutdown menu and there it is.

Does anyone have any idea why this works and how I can ensure that my soundcard stays around after a power down?

---

### Post by SoundMind on 2008-01-15
A thought: What if, on power up, the PCI slot belonging to the card is started up late enough, which in turn means the the card, itself, does not register the existence of the breakout box until it is too late for Ubuntu to look for it. Therefore, the ice driver is loaded for the card itself, since it is seen on startup, but the breakout box is a spit second (or a few seconds) behind and it is not registered and not loaded. On restart, the OS restarts, but nothing loses power, so the soundcard is now seen by Ubuntu and all (or rather most, as ICE takes some hacking to get the whole card, from what I've read) is loaded properly.

Does that seem plausable to anybody? If so, can anybody think of a BIOS setting that might change this?

---

