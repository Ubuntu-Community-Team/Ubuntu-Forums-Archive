---
title: "freezing problem"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by baskettplayr on 2007-05-31
i dont know why but i will be on ubuntu with maybe like 2 programs open and it will freeze or sumtime it will freeze on the screen saver  i dont think its my ram i have 512 and a 3.33 ghz proccer i dont know if thats good but could someone help?

---

### Post by lazyart on 2007-05-31
what video card are you using?

---

### Post by Sparkster185 on 2007-05-31
Your hardware is definitely able to handle Ubuntu.  I'm guessing the problem lies in the graphics card/driver (especially since it freezes after a screensaver runs).

Can you try opening the SystemMonitor and sorting by CPU usage?  That will tell you which process, exactly, is making it run slow/freeze.  If it's Xorg, the I bet you don't have the proper driver installed.

Which graphics card do you have?

---

### Post by Cypher on 2007-05-31
What version of Ubuntu, has it always been happening? Did it start happening after an update?

---

### Post by baskettplayr on 2007-05-31
um idk what i have but on my windows i had to install a intel graphic accerator but i never installed a driver for it on u buntu...

---

### Post by baskettplayr on 2007-05-31
how do i find what kind of graphics card do i have

---

### Post by Sparkster185 on 2007-05-31
I also have an intel graphics card in my laptop and it worked beautifully out of the box.

"lspci -v | less", then scroll down until you find something relating to graphics.

---

### Post by baskettplayr on 2007-05-31
i typed that in and this is what i got...
[/QUOTE]

then on another thread a kid said i needed to type "lspci -v | less", then scroll down until you find something relating to graphics... and i did and this is what i got ..... > 00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller
 Hub (rev 04)
        Subsystem: Gateway 2000 Unknown device 4038
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated 
Graphics Controller (rev 04) (prog-if 00 [VGA])
        Subsystem: Gateway 2000 Unknown device 4038
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at 30200000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at ffe0 [size=8]
        Memory at 20000000 (32-bit, prefetchable) [size=256M]
        Memory at 30280000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High
 Definition Audio Controller (rev 03)
        Subsystem: Gateway 2000 Unknown device 4038
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at 302c0000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

what does this mean? is it installed already or do i  need to install it?

---

### Post by baskettplayr on 2007-05-31
bump

---

