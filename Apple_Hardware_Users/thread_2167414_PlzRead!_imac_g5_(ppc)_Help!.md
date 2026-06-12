---
title: "*PlzRead!* imac g5 (ppc) Help!"
date: 2013-08-13
forum: Apple Hardware Users
---

### Post by jared_marshall on 2013-08-13
I have a 17" ppc with a 1.6ghz g5 proccessor with 1gb ram I have had leopard on this machine but now that leopard is unsupported I have tried to install ubuntu live/desktop (ppc ) and have had no success when I boot from the cd I get into yaboot (not sure if spelled correct) I have tried every command that's availabe when I press tab but the proccess always ends up the same I get stuck at the low graphics mode screen that tells me to reconfigure later I press ok, then a new list appears I tried everything on that list but it always just brings me back to something like a list and to the right of the list its says ok next to each item listed, the install will hang here and not do anything, possiably should I try a different iso? What am I doing wrong? And yes I could try burning a new iso if that's my problem

---

### Post by QIII on 2013-08-13
*Moved to **&#8203;Apple Users***

---

### Post by lukeiamyourfather on 2013-08-13
It sounds like you're running from the live disc, and it's warning you about the graphics because you probably have an older graphics card. There should be an item from the applications menu to install Ubuntu to the hard drive. However that low graphics warning might always be there since Unity (Ubuntu's interface) is meant to run on newer graphics cards. I would say try a variant of Ubuntu that doesn't require a newer graphics card like Lubuntu (uses LXDE interface) but there's no PPC version of Lubuntu (or Xubuntu, Xfce).

Since this is an Ubuntu forum I hate to say it, but another distribution might be more fitting for the older PPC hardware. Maybe Debian with LXDE? Puppy Linux would be good, but again, no PPC version that I know of. I think the biggest limiting factor is going to be the PPC architecture because only a few distributions support it these days. If you don't want to go through that much trouble to get it working, maybe go spend $100 on a used PC from a local computer shop and install Ubuntu on it.

---

### Post by jared_marshall on 2013-08-13
Well I have a really good pc at the moment I just wanted to try linux on a computer I am nevrr going to use as a test but now I am dessperate to get it to work, the reason I am here is because other people say they have gotten it to work on my specific machine if you could or anyone for that matter send me a link to a fairly good linux distro that I could use or find a solution for me to run it on my ppc

---

### Post by lukeiamyourfather on 2013-08-13
Wait! There ***_is_*** a PPC version of Lubuntu! It was just not on the main page for Lubuntu. Try the one titled "lubuntu-13.04-desktop-powerpc.iso" and see if that works for you.

[http://cdimage.ubuntu.com/lubuntu/releases/13.04/release/](http://cdimage.ubuntu.com/lubuntu/releases/13.04/release/)

---

### Post by jared_marshall on 2013-08-13
what's the maib differnce I will be givingup if go with lubuntu instead of ubuntu

---

### Post by jared_marshall on 2013-08-13
Also if you guys didn't know the g5 is 64bit

---

### Post by lukeiamyourfather on 2013-08-13
Yes, the G5 is 64-bit, but it's not the 64-bit Ubuntu is talking about on the download page. When someone says 64-bit in reference to a Linux distribution or software they usually mean [x86-64 (amd64)]("http://en.wikipedia.org/wiki/X86-64"). What you're talking about is [ppc64]("http://en.wikipedia.org/wiki/Ppc64") which is different.

Ubuntu and Lubuntu are the same under the hood, but Lubuntu uses LXDE instead Unity. LXDE stands for Lightweight Desktop Envrionment. Unity is the default interface on Ubuntu (and only Ubuntu) which requires a graphics card and drivers with 3D acceleration. Functionally both Ubuntu and Lubuntu will do the same stuff but Lubuntu won't complain about the graphics card and isn't as much of a resource hog.

---

### Post by jared_marshall on 2013-08-13
Will it still be able to use most of the same core featurses? And will the appstore etc be on it?

---

### Post by blackbird34 on 2013-08-14
Yes, Lubuntu will be able to do everything that vanilla Ubuntu can, only faster, and with less whizz-bang graphical effects. I believe the appstore has been renamed to "Lubuntu Software Centre" instead of "Ubuntu Software Centre", and is lighter too, but it will have everything you need. Also, some of the default applications are different (lighter ones), but you can get the ones you want or lack (e.g LibreOffice, VLC...) from the repositories/ appstore.

---

### Post by pauljwells-m on 2013-08-14
Keep trying, it can work very well! I just did it on my G5 Powermac with NVidia 6600LE card (one of the least-friendly) take a look at my post here [http://ubuntuforums.org/showthread.php?t=2166837&p=12753950#post12753950](http://ubuntuforums.org/showthread.php?t=2166837&p=12753950#post12753950)

---

### Post by jared_marshall on 2013-08-14
Hey ok so I have tried out lubuntu but I get stuck at a pixel clock or smething cannot be found can anyone help or guide me through the install? (:

---

