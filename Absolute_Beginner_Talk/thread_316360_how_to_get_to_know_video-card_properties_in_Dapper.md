---
title: "how to get to know video-card properties in Dapper?"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by 1002285 on 2006-12-10
I am selling an old computer and it has Dapper as only OS right now. I was asked "how many Mb-s video card?". Where can I find the answer?

---

### Post by dorcssa on 2006-12-10
I thought it would be in system >administration >device manager, but I've looked after it, and I couldn't find the answer there. Maybe in BIOS setup?

---

### Post by nickpaton on 2006-12-10
It's a very long list but check the output of:

```
sudo lshw
```

It's near the top under "*-display" section.

---

### Post by 1002285 on 2006-12-11
> **nickpaton said:**
> It's a very long list but check the output of:

```
sudo lshw
```

It's near the top under "*-display" section.

Thank you. So it's 16 Mb?

    *-display
                description: VGA compatible controller
                product: NM2200 [MagicGraph 256AV]
                vendor: Neomagic Corporation
                physical id: 0
                bus info: pci@01:00.0
                version: 20
                size: 16MB
                width: 32 bits
                clock: 33MHz
                capabilities: vga bus_master cap_list
                resources: iomemory:f9000000-f9ffffff iomemory:fdc00000-fdffffff

---

### Post by bodhi.zazen on 2006-12-11
Looks like 16 Mb to me as well....

---

### Post by 1002285 on 2006-12-11
> **bodhi.zazen said:**
> Looks like 16 Mb to me as well....
Is there any chance that this output could be wrong? I don't even know whether 16 Mb is very bad or not, but this computer has been able to show videos both in Windows XP and Dapper.

---

### Post by bodhi.zazen on 2006-12-11
I suppose it is possible, but this it seems unlikely....

This is your video ram and although I am not a hardware expert the last time I ran a low video ram box, as I recall, your regular ram will "fill in". I thought this was an advantage of ram on a video card (frees up ram ram).

I could be wrong.

---

### Post by Papillonrus on 2007-01-16
The neomagic magicgraph 256AV NM2200 has only 2.5MB of ram.  Used mostly in laptops.

---

