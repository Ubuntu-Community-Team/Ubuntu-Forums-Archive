---
title: "desktop effects and 3d games"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by graigsmith on 2007-04-19
so, i had been running wow in linux with my ati 9200.  and i can turn on the desktop effects and they are really cool but i cant seem to use them at the same time.  is there anyway to fix this?  would getting an nvidia card help this?  

oh, videos often have problems when the 3d effects are on.

---

### Post by igknighted on 2007-04-19
> **graigsmith said:**
> so, i had been running wow in linux with my ati 9200.  and i can turn on the desktop effects and they are really cool but i cant seem to use them at the same time.  is there anyway to fix this?  would getting an nvidia card help this?

I think the issue is that you have an old video card.  It probably cannot handle multitasking well.  If you do get a new one go for nvidia though.

NOTE: I am assuming since you are calling it desktop effects that you are using the open-source driver and aiglx, as that is the only way to use desktop effects.  If you are using fglrx and XGL then XGL is your issue, try the open-source driver.  You can use beryl-manager to quickly switch between metacity (the nomal gnome window manager) and beryl's 3d window manager for gaming to save time.

---

### Post by graigsmith on 2007-04-19
i actually have an ati x800.  But ati's drivers are so poor i'd rather not use it.  i tried it and when i switched to another terminal and tried to switch back, it froze up.

how good are nvidia's drivers, nice and stable?   can you switch to terminals? ie alt-ctrl f1?

---

### Post by aktiwers on 2007-04-19
Back when I used an ATI 9200 even the 3d effects (beryl or XGL or whatever it was called then) was slow. I changed to Nvidia 6200 and its running great! Though Counterstrike Lags a little with Beryl turned on.

I too think its a mix of bad driver support, and simply because your card is old.

---

### Post by aktiwers on 2007-04-19
> **graigsmith said:**
> i actually have an ati x800.  But ati's drivers are so poor i'd rather not use it.  i tried it and when i switched to another terminal and tried to switch back, it froze up.

how good are nvidia's drivers, nice and stable?   can you switch to terminals? ie alt-ctrl f1?

Yeah you can! and they are a lot better than ATI's drivers. Seriously.. I spend about 400kr ($55) on my Nvidia card and I have never been happier. They are also a lot easier to install, and dont break all the time. 

I would really recommend switching to Nvidia!

---

### Post by igknighted on 2007-04-19
> **graigsmith said:**
> i actually have an ati x800.  But ati's drivers are so poor i'd rather not use it.  i tried it and when i switched to another terminal and tried to switch back, it froze up.

how good are nvidia's drivers, nice and stable?   can you switch to terminals? ie alt-ctrl f1?

Weird, I have an x800 and have found the drivers to be perfect.  I used the open source radeon drivers mostly, but even when I did use fglrx they were fine (although they did not work well with wine apps, I will say that).  Nvidias are better than ATI for the commercial, but the fact that there are working 3d drivers that are open source for ATI is a plus.  A binary blob of a driver isn't a good solution no matter what.  But again, nvidias blib is a little better than ATI's.

---

### Post by graigsmith on 2007-04-19
so, what's the best nvidia card thats for AGP that i can get?

---

### Post by kornhead127 on 2007-04-19
I think its bad setup. I run desktop effects beatifully. And I play CS, Half-Life  2, and CS:S, on a Radeon 7000. Learn all there is to know about your driver and take full advantage of it.:)

---

### Post by graigsmith on 2007-04-19
well, the open source drivers for my ati 9200 work with wow.  the opensource drivers for the x800 don't work with wow. and neither did ati's proprietary drivers.  it just gave an error.  plus theres the ati driver crashing issue.

---

