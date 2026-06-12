---
title: "No sound; help"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by gingerbreadman on 2007-06-03
Nothing really new to these forums, but I am yet another in need of sound help.

Basically I can't get sound to work. Nothing works. The default speakers, plug in headphones, usb speakers, and microphones don't work.  I have everything unmuted in ALSA mixer, and have even done everything in the [HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto") guide.

All of my sound devices are detected, but nothing works. cant seem to find a reason.

I run <lspci -v> and get the following for sound:

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: NEC Corporation Unknown device 8309
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at 331c0000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0

any help appreciated

---

### Post by zvacet on 2007-06-03
Did you install codecs?

[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

---

