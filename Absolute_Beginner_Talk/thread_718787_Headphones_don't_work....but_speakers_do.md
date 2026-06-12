---
title: "Headphones don't work....but speakers do"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by gkrules on 2008-03-08
I am on ubuntu 7.10 and whenever i go to listen to something on my headphones no sound comes out, i have tried multiple headphones but none work. I remember they used to work on Vista... I have a Conexant HD Audio SmartAudio 221 sound card. The speakers work fine, but no sound comes out of the headphones at all.


When I did 

```
lspci -v
```

I got this for the audio:

```
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
        Subsystem: Hewlett-Packard Company Unknown device 30ea
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
        Memory at f6480000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
```

i know for sure i have a conexant 221

---

### Post by justsomedude on 2008-03-08
Maybe they're just muted. Open a terminal and type

```
alsamixer
```

to check if they are. You can use the arrow keys to navigate to the right, if the setting is hidden.

---

