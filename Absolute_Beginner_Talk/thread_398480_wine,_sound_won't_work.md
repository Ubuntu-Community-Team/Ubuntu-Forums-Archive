---
title: "wine, sound won't work"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by Sasa_Ivanovic on 2007-04-01
Sound ussualy works in Ubuntu but i can only play one sound at once, unlike in Windows. Anyhow i noticed that sound doesn't work in wine. So i ran winecfg, then i clicked at the "Sound" tab, the app exited and here's what i got :
```

sasa@Kanta:~/.wine/drive_c/Program Files/Dark Ages II$ winecfg
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
Creating link /home/sasa/.kde/socket-Kanta.
can't create mcop directory

```
could you help me out ?

---

### Post by Sasa_Ivanovic on 2007-04-01
here's what this command ```
lspci -v
```
returned
```

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: Giga-byte Technology Unknown device a002
        Flags: bus master, fast devsel, latency 0, IRQ 169
        Memory at e5000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

```

---

