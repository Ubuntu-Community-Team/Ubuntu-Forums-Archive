---
title: "No Sound with a CMI8788 Chip!"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by Der Doktor on 2006-12-26
Hi!

I want to use the 3D Theatron DTS Sound Card under Drapper Drake (32 Bit)! It uses the CMI8788 chip by C-Media! This should work under ALSA (So says the website...) but it doesn't! :(

Please help me!

---

### Post by Azakus on 2006-12-26
Do you have onboard sound? If you do, go into your BIOS on your motherboard and turn it off. The sound daemon defaults to onboard sound, so turning it off will default it to your new soundcard.

---

### Post by Der Doktor on 2006-12-26
Yes, I have Onboard Sound! But when I disable it, I don't hear anything with the other soundcard!:neutral:

---

### Post by Azakus on 2006-12-26
Here you go
[Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound")

---

### Post by Der Doktor on 2006-12-26
lspci -v  lists:
> 04:09.0 Multimedia audio controller: C-Media Electronics Inc Unknown device 8788
        Subsystem: C-Media Electronics Inc Unknown device 8788
        Flags: bus master, medium devsel, latency 32, IRQ 10
        I/O ports at 9c00 [size=256]
        Capabilities: <access denied>

But I can't find drivers for CMI8788 Chips at [alsa-project.org]("http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-C-Media#matrix"), although the C-Media page says so...:-?

---

### Post by Azakus on 2006-12-26
That list hasn't been updated since 2005. I'll bet that the ALSA drivers have it, so continue with the guide.

---

### Post by Der Doktor on 2006-12-26
> I'll bet that the ALSA drivers have it, so continue with the guide.
That sounds good! ;)
But when I try sudo modprobe snd-cmipci nothing happens...

---

