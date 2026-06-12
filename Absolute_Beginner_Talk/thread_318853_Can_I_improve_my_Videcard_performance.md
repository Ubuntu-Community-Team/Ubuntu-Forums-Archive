---
title: "Can I improve my Videcard performance"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by dkenny on 2006-12-14
All
I just ran the FPS test on my videocard using
glxgears -printfps

Here are the results
7588 frames in 5.0 seconds = 1517.598 FPS
7589 frames in 5.0 seconds = 1517.698 FPS
7589 frames in 5.0 seconds = 1517.676 FPS
7583 frames in 5.0 seconds = 1516.496 FPS
9572 frames in 5.0 seconds = 1914.233 FPS
7571 frames in 5.0 seconds = 1514.123 FPS
7589 frames in 5.0 seconds = 1517.691 FPS
7660 frames in 5.0 seconds = 1531.910 FPS

I've heard that anything under 2000 is pretty poor. IS there a way for me to get better performance out of this card? I'd rather not buy a new one just now.



here's the details on my video card

0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)] (prog-if 00 [VGA])
        Subsystem: ATI Technologies Inc: Unknown device 0302
        Flags: bus master, fast devsel, latency 0, IRQ 169
        Memory at d0000000 (32-bit, prefetchable) [size=128M]
        I/O ports at dc00 [size=256]
        Memory at dfde0000 (32-bit, non-prefetchable) [size=64K]
        Expansion ROM at dfe00000 [disabled] [size=128K]
        Capabilities: <available only to root>

0000:01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]
        Subsystem: ATI Technologies Inc: Unknown device 0303
        Flags: bus master, fast devsel, latency 0
        Memory at dfdf0000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <available only to root>

---

### Post by pay on 2006-12-15
Install the fglrx driver [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

---

### Post by dkenny on 2006-12-15
Thanks for the link. It does, however, refer to Edgy - it this same process applicable in Dapper?

---

### Post by Kobalt on 2006-12-15
No, it's not. Here is the procedure for Dapper : 
[http://ubuntuforums.org/showthread.php?t=143283](http://ubuntuforums.org/showthread.php?t=143283)

---

### Post by pay on 2006-12-16
Here's the Dapper installation method. (sorry i rush read your post) [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

---

