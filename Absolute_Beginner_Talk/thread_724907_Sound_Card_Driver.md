---
title: "Sound Card Driver"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by perito on 2008-03-15
Im running Ubuntu 7.04 on a toshiba satellite laptop, I hear nothing, but I guess its a sound card driver problem. so how can I know what sound card do i have? and where can i download and install its corresponding driver?
thx

lspci -v gives this
```

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at f0b40000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

```

---

### Post by Chemist on 2008-03-15
the link below will take you to the ALSA project page. I notice that the ICH7 family is support 

there are details on which drivers you need to install

[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel) 

hope this helps amte

---

### Post by superprash2003 on 2008-03-17
try this... [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

