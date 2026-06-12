---
title: "[SOLVED] Compiz slow after restart (was fast at installation)"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by jaredssix on 2008-01-19
Hey all,
I just installed compiz and launched the cube, wobblies, etc.
Everything was super clean and fast until I restarted, and now all the graphics are slow--even typing is slow!

What did the restart miss?

I should add that the cube is fast; the windows effects are slow.

My card is intel 915, which I would guess is rather minimal--but everything looked so good until the restart!

--Jared

---

### Post by nikoPSK on 2008-01-19
did you mess with xorg? :)

---

### Post by jaredssix on 2008-01-19
I did run through the xorg config, but (at least attempted to) stuck with all the defaults.

---

### Post by DutyDuty on 2008-01-19
In CCSM, make sure Resize Windows setting is "Stretch". Other tend to slow it considerably (in my experience.)

---

### Post by jaredssix on 2008-01-19
Duty,
That helped bunch--but effects (and typing) still aren't fluid like they were before the reboot!

---

### Post by mike-laptop-dot-local on 2008-01-19
In the Compiz Config Settings Manager, click 'General Options', then click its 'Display Settings' tab. Check/uncheck the "Sync to vBlank" box and see if that helps.

For me, checking the vBlank box always significantly reduces the CPU time for compiz.real

---

### Post by jaredssix on 2008-01-19
Mike! That worked fantastically! But only for a minute.

Upon restart, a brief window came up informing me Nautilus had been disabled. My desktop/wallpaper were nowhere in sight (a nice effect with the cube) and all the cube and windows effects were fast and fluid.

Then it froze. I restarted and my desktop/wallpaper are back, and the graphics are slow . . .

But I think you're on to something!

---

### Post by jaredssix on 2008-01-19
Thanks everyone,
It appears all is well after a complete uninstall, reinstall--even the fast and fluid bit which started all this (4 hrs ago)!

---

### Post by nikoPSK on 2008-01-19
please mark this "SOLVED". :)
Thread tools, mark this thread as "SOLVED".

nikoPSK

---

### Post by jaredssix on 2008-01-19
After compiz reinstall, the update manager had a few things to add.

Also, keep/set both transparent cube opacities (in ccsm) to 100--any opacity resulted in slower graphics for me.

---

