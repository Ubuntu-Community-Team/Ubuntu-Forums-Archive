---
title: "Crazy Keyboard!"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by srt5 on 2007-05-14
Since installing Beryl I have been having some annoyances with my keyboard layout. I set the default layout when I first installed Ubuntu (the standard United Kingdom layout), and I didn't have any problems.

The first time I logged into my Beryl desktop, it asked me something to do with the keyboard layout, and I think I may have checked a box that said something like "Keep X keyboard configuration" (sorry for the ambiguity, but I can't remember the dialog word for word!). Anyway, each time I log into Ubuntu, my keyboard configuration is set to some weird layout, and I have to keep changing the layout back to UK by going to.. 

System > Preferences > Keyboard

Is there anyway to stop Beryl from overriding my keyboard layout configuration each time I log in? Any help that you could provide would be much appreciated because this problem is so frustrating!!

Thanks :)

---

### Post by overdrank on 2007-05-14
> **srt5 said:**
> Since installing Beryl I have been having some annoyances with my keyboard layout. I set the default layout when I first installed Ubuntu (the standard United Kingdom layout), and I didn't have any problems.

The first time I logged into my Beryl desktop, it asked me something to do with the keyboard layout, and I think I may have checked a box that said something like "Keep X keyboard configuration" (sorry for the ambiguity, but I can't remember the dialog word for word!). Anyway, each time I log into Ubuntu, my keyboard configuration is set to some weird layout, and I have to keep changing the layout back to UK by going to.. 

System > Preferences > Keyboard

Is there anyway to stop Beryl from overriding my keyboard layout configuration each time I log in? Any help that you could provide would be much appreciated because this problem is so frustrating!!

Thanks :)

HI I think   *sudo dpkg-reconfigure xserver-xorg* is going to be your best bet and then setup up beryl again. Well that is my thoughts but I do not use feisty! :)

---

### Post by srt5 on 2007-05-15
reconfiguring xorg again and re-installing beryl would probably solve my problem, but isn't there some configuration file i could just modify to stop it from changing back all the time? that would seem like a lot less hassle. any suggestions? :)

---

