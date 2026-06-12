---
title: "Blue and pink gibberish on the TV"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by puterboy on 2007-11-26
Hello. Having some problems. I'm watching a movie (DivX, using Totem and w32codecs). I am putting the video onto my TV via an S-Video cable. After a couple episodes, the video on the TV turns into green and pink gibberish, only within the player. The Ubuntu background is fine. If I drag it back onto my monitor, the picture is clear, but frozen. Sound works all throughout. Any ideas on what's happening? Thanks in advance for help

---

### Post by master_kernel on 2007-11-26
Can you post your video card/computer specs? Also try dmesg | tail to see what that comes out with.

---

### Post by puterboy on 2007-11-26
[   54.468000] Clocksource tsc unstable (delta = -62597667 ns)
[   56.120000] agpgart: Found an AGP 3.1 compliant device at 0000:00:00.0.
[   56.120000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   56.120000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[38470.132000] agpgart: Found an AGP 3.1 compliant device at 0000:00:00.0.
[38470.132000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[38470.132000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[39440.504000] agpgart: Found an AGP 3.1 compliant device at 0000:00:00.0.
[39440.504000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[39440.504000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode


Video card is an nvidia 6600gt. Any other specs u need?

---

### Post by puterboy on 2007-11-27
Found the problem, still working on a solution. Problem is that the CPU changes frequencies, which then causes the video mode to be considered unstable. The PC then switches to an alternate mode, which doesn't seem to support TV-OUT for me.

---

