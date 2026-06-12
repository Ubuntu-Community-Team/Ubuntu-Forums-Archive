---
title: "Inspiron 1521 sound problem"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by grfalk on 2008-02-27
Installed Ubuntu on an originally Vista machine. All works fine, except for the sound card. None is detected. 
 
aplay -l results in:
        aplay: device_list:204: no soundcards found...
lspci -v results in: 
        00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
        Subsystem: Dell Unknown device 01fc
        Flags: slow devsel, IRQ 17
        Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

Cannot find the driver on the alsa site. 

Any help would be appreciated.

---

### Post by superprash2003 on 2008-02-28
try this..may work [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

