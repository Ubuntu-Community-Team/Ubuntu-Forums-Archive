---
title: "Your recommendations..."
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by kane77 on 2006-12-28
what I need to do...

I have this PC
Duron 1400Mhz
128 MB RAM (!!!)
onboard graphics card (S3 Savage)

I need (want) to install linux.. I tried installing xubuntu, (only the alternate cd worked), but it doesn't have 100% localization (english is no problem for me, but my dad, whose computer it is wants it in slovak)... so basicaly its mixture of both slovak/english...
Also, for some unknown reason a window (any window) leaves a rectangle (of itself) in upper left corner... installing drivers for graphic card might help, but I couldnt find one..

What would you suggest? Something different then ubuntu? (I like ubuntu a lot... I use it on my computer, but mine is athlon64 3800+ with 1 Gb ram... so there's no problem...)

Do you think installing ubuntu (with gnome) would be suicide on the machine I specified? (it only has 128 megs of ram...)

---

### Post by pseudonym on 2006-12-28
Gnome would run a bit slow on that machine, I think. Plus I'm not sure it would solve your localisation issue (but I'm not 100% sure on that one).

You could improve your video by reconfiguring xserver-xorg to use the 'S3' driver instead of 'vesa' which I suspect it is using now...

PS - For a modest investment on ebay you could also buy a cheap video card - if the motherboard has an AGP slot get one of those, otherwise a 32MB PCI one will do. Plus of course an extra 128MB stick of RAM would help a lot.

---

### Post by wpshooter on 2006-12-28
You could give it a shot with the ALTERNATE CD, but with that amount of memory it MAY be a no-go.

---

### Post by amo-ej1 on 2006-12-28
i have a dapper installed on a pIII 850 Mhz with 128meg ram, and it was still bareable. Altough I tuned most settings for performance. Disabled as many graphical things, services, ... etc as possible. And nowadays the machine is still used for firefox and thunderbird without any problems (and with some patience). 

But don't expect it to run openoffice or things like that in a smooth way ;)

but why not spend 10$ or so and get some extra ram on ebay or something like that ?

---

### Post by kane77 on 2006-12-28
> **pseudonym said:**
> You could improve your video by reconfiguring xserver-xorg to use the 'S3' driver instead of 'vesa' which I suspect it is using now...

I did.. only I used savage driver... but I dont think I saw any performance boost..

---

### Post by pseudonym on 2006-12-28
> **kane77 said:**
> I did.. only I used savage driver... but I dont think I saw any performance boost..
It's probably only got 4MB video RAM, right? I ran Debian on an old PII with a Savage onboard video and the video was exactly that - savage :) . A cheap PCI video card off ebay solved my problem, however.

---

