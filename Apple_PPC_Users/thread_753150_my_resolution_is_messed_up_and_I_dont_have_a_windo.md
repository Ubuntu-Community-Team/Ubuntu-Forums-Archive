---
title: "my resolution is messed up and I dont have a window decorator"
date: 2008-04-12
forum: Apple PPC Users
---

### Post by zeus123 on 2008-04-12
Ive just bought an ibook g4 and installed xubuntu onto it.

I updated the 6.06 to 8.04. everything worked well. Then I installed xgl, compiz and emerald.

Compiz didnt work well because it was slow and emerald wouldnt decorate correctly. I changed my xorg.conf so that xubuntu used the radeon driver and not the ati driver (I heard this can help performance issues) 
The only difference it made was a smaller resolution.

So I out xorg.conf back to the way it was, unistalled emerald, compiz and xgl and restarted the laptop.

I still have the low resolution and dont have a window decorator.

Does anyone know what I might have to do to fix this?
Im about to reinstall 6.06 and update to 8.04 again. It takes hours and I dont want to do that.
Help!

Many Thanks
Rik

---

### Post by zeus123 on 2008-04-12
no worries, sussed it.

---

### Post by stream303 on 2008-04-12
Cool!  Glad you got it, although many of us with nvidia cards have no capability for fancy graphics like Compiz etc due to the lack of manufacturer's specs for the developers.

That xorg.conf in 8.04 is pretty freaky!

---

### Post by BladeMelbourne on 2008-04-12
It's worth noting that if you specify:
```
        Driver          "ati"
```

ati_drv will load radeon_drv automatically. I believe ati_drv is like a wrapper for radeon_drv, mach64_drv and r128_drv.

That said, I run with:
```
        Driver          "radeon"
```
without any problems.

---

