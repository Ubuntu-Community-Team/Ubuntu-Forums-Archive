---
title: "sound is missing"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by gregcha117 on 2008-04-06
Since 2.6.24-12 my sound doesnt work I tryed an older kernel which worked for a short while then again my sound went. I waited for a kernel upgrade hoping it would solve my problem but still 2.6.24-15 has no sound for me. I tryed inserting drivers using depmod to 2.6.24-12 when I was on that and older modules but I'm not sure if i did it right but it didnt work anyways and I'm guessing with the new kernel thats irrelevant

Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
Subsystem: ABIT Computer Corp. Unknown device 1c13
Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
I/O ports at f000 [size=256]
I/O ports at ec00 [size=256]
Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
Capabilities: <access denied>

alsamixer picks up my sound device but no sound comes out my speakers, it works on XP but ugh i want ubuntu with sound

---

### Post by AlexParky on 2008-04-06
Are you running an HP dv9000 series laptop, by any chance?

---

### Post by gregcha117 on 2008-04-06
nope, i have a desktop computer

---

### Post by Denvercobra on 2008-04-06
This worked for me.
Type in" Alsamixer" in the terminal, then make sure all the values are at 100 percent.

---

### Post by gregcha117 on 2008-04-07
i already tryed alsamixer in terminal, it works normal everything is set properly but i still have no sound

---

