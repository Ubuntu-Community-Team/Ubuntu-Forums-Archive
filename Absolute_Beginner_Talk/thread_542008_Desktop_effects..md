---
title: "Desktop effects."
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by CapitanYochua on 2007-09-03
anyone have a link to check if my video card will let me use the desktop effects?

---

### Post by tgunner on 2007-09-03
What is it? Pretty much any semi modern card will work.

---

### Post by CapitanYochua on 2007-09-03
I forgot which command I use to check what video card I have. What is it?

---

### Post by Sbarton on 2007-09-03
Try in terminal    ```
 lspci
```
regards

---

### Post by CapitanYochua on 2007-09-03
I got a long list of my hardware. So I just paste binned it all to make sure I don't tell you the wrong information.
[http://paste.ubuntu-nl.org/36214/plain/](http://paste.ubuntu-nl.org/36214/plain/)

---

### Post by sumguy231 on 2007-09-03
Try 'lshw -class display' instead to get the specifics of your video card.

Example output from my computer:
```
  *-display
       description: VGA compatible controller
       product: NV18 [GeForce4 MX 4000 AGP 8x]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@01:00.0
       version: c1
       size: 64MB
       width: 32 bits
       clock: 66MHz
       capabilities: vga bus_master vga_palette cap_list
       configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5
       resources: iomemory:ec000000-ecffffff iomemory:e8000000-ebffffff irq:21

```

---

### Post by Officer Dibble on 2007-09-03
> **CapitanYochua said:**
> I got a long list of my hardware. So I just paste binned it all to make sure I don't tell you the wrong information.
[http://paste.ubuntu-nl.org/36214/plain/](http://paste.ubuntu-nl.org/36214/plain/)

This one is your video card:

> 01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)

I couldn't get drivers for the S3 Unichrome in my wifes machine so I can't tell you whether it would work or not sorry... but there are much wiser personages here than me... so hang fire... :)

---

### Post by CapitanYochua on 2007-09-03
*-display               
       description: VGA compatible controller
       product: VT8378 [S3 UniChrome] Integrated Video
       vendor: VIA Technologies, Inc.
       physical id: 0
       bus info: pci@01:00.0
       version: 01
       size: 64MB
       width: 32 bits
       clock: 66MHz
       capabilities: vga bus_master cap_list
       configuration: latency=32 mingnt=2
       resources: iomemory:e4000000-e7ffffff iomemory:e8000000-e8ffffff irq:21

---

### Post by SOULRiDER on 2007-09-03
You wont be able to do much with an oboard card... =/

---

### Post by insane_alien on 2007-09-03
i'd say give it a shot. you can always disable it again if it doesn't work perfectly. my integrated graphics chip on my thinkpad can run it fine and it can only take 32MB of shared memory. its clock is also set to 33MHz.

---

### Post by Sbarton on 2007-09-03
I'm sure someone more experienced in graphics will answer you, but a quick glance I would say this would not be good enough for Desktop Effects.
regards

---

### Post by CapitanYochua on 2007-09-03
So, just go to desktop effects and click it. If it doesn't work. There is nothing else I can do?

---

### Post by insane_alien on 2007-09-03
if it does't work then you can always buy a proper graphics card, unless you're on a laptop. if you are on a PC a cheap graphics card will do. a nVidia FX5200 will run everthing. and i've seen one on ebay for £5 once.

---

### Post by CapitanYochua on 2007-09-03
I only have the wobble windows or something as a desktop effect. Which doesn't work. I've seen in the past this computer do like water looking effect (when my brother had it).

---

### Post by insane_alien on 2007-09-03
thats beryl(well, now compiz-fusion). i'm not sure if you can do it with the default desktop effects.

is that even a full version of compiz?

---

### Post by Paul133 on 2007-09-03
I don't think so. If you really want desktop effects, you should install Compiz Fusion.

---

### Post by sailor2001 on 2007-09-03
[http://ubuntuforums.org/showthread.php?t=508769](http://ubuntuforums.org/showthread.php?t=508769)     when I want to turn on compiz, I alt/f2 and type compiz --replace   and to go back to metacity it's metacity --replace

---

### Post by CapitanYochua on 2007-09-03
So how do I use Compiz?

---

### Post by mlyons16 on 2007-09-04
Ya, i just watched this video:

[http://www.youtube.com/watch?v=E4Fbk52Mk1w](http://www.youtube.com/watch?v=E4Fbk52Mk1w)

I like these desktop effects. How do I install them?

---

### Post by mlyons16 on 2007-09-04
How do I install/activate Compiz Fusion effects from this website:

[http://ubuntuforums.org/showthread.php?t=508769](http://ubuntuforums.org/showthread.php?t=508769)

---

### Post by ncalvin on 2007-09-04
I'm running an ATI Radeon X1300 (512 MB) and still can't run desktop effects (or beryl for that matter). I have no idea as to why.

---

