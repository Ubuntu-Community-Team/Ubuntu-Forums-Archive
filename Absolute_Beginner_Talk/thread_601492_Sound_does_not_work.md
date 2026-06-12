---
title: "Sound does not work"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by evillan on 2007-11-03
Sound does not work under 7.10.

I booted a live CD with 7.04 and the sound worked - so it's not a hardware problem.
What do I do?

sudo lscpi -v output:
```

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Subsystem: Fujitsu Siemens Computer GmbH Conexant softmodem SmartCP
	Flags: bus master, fast devsel, latency 0, IRQ 23
	Memory at dc240000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Unknown type IRQ 0

```

---

### Post by daimaru on 2007-11-03
i also have the Conexant audio thing, for me i just had to go to system-->pref-->sound on devices tab set all the stuff from autodetect to "Conexant Analog" . and sound worked. btw Conexant digital did not work.

---

### Post by evillan on 2007-11-03
> **daimaru said:**
> i also have the Conexant audio thing, for me i just had to go to system-->pref-->sound on devices tab set all the stuff from autodetect to "Conexant Analog" . and sound worked. btw Conexant digital did not work.

It does do it for my laptop. Tried all the other options, none of them worked.

Other good ideas?

---

### Post by evillan on 2007-11-03
Nevermind, tried gnome-alsamixer, works now.

---

