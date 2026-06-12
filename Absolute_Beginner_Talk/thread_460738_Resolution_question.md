---
title: "Resolution question"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by Exershio on 2007-06-01
I have an intel chipset with onboard video (no graphic card), and here's my question: Does using a higher resolution consume more CPU/RAM (for example, using 1280x1024 rather than 1024x768 )

---

### Post by AtrejuT on 2007-06-01
as far as I know it does, since your onboard graphics adapter uses shared memory, so that means it uses parts of your normal RAM. It needs to save an image of your desktop in the ram, so if you increase the resolution you also increase the size of that image.

---

### Post by Exershio on 2007-06-01
Thanks for the reply. One more question: Is the memory/performance difference between 1152x864 and 1024x768 noticable? I only have 256mb of ram, and I'm using Xubuntu. I just don't want to do anything that noticeably lowers speed.

---

### Post by AtrejuT on 2007-06-01
you can do a quick calculation yourself:
at 24 bits color depth
1024*768*24 = 18874368 bits = 2304 kB.
1152*864*24 = 23887872 bits = 2916 kB.

So both is not a whole lot. It might be twice as much for each one, because you have two buffers and stuff, but still running say, beagle or such takes a whole lot more ram. So I'd always go for the higher resolution, but then, I'm a big fan of high res screens.

By the way, if you're using a LCD monitor you should _really_ run it at its native res, anything else looks plain ugly!

---

### Post by Exershio on 2007-06-01
Okay, thanks a lot for your help. I'll stick with 1152x864 then (it's the highest decent resolution I can get on my 17" CRT monitor.)

---

