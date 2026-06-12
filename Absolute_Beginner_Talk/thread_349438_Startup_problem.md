---
title: "Startup problem"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by Auria on 2007-01-30
Hi, i reconfigured X and have done something wrong - now my computer won't boot anymore. After the progress line, i get a black screen.

How can i just bring up a terminal to reconfigure X? I tried ctrl-alt-bckspace and clrt-alt-F2, nothing happens :(

I also tried to boot from the live CD' but can't seem to get it to reconfigure the X configuration of my hard disk

---

### Post by jkeyes0 on 2007-01-30
When booting your computer up, there should be a brief few seconds where you can hit ESC on your keyboard to go to the Grub menu (before Ubuntu actually goes through its loading screen). There should be a recovery or safe mode type option there as a secondary boot option. Try that one out.

---

### Post by Auria on 2007-01-30
Hi, when are these few seconds?

After yaboot asks me which partition to boot on? It doesn't sound clear to me when is that

---

### Post by Auria on 2007-01-30
I just tried booting and repeatedly pressing ESC at all times

nothing showed up :(

what can i do??

EDIT: is Grub the boot manager? Mine is yaboot

---

### Post by Auria on 2007-01-30
bump (please, i took hours and hours just to succeed setting up a half-working system... don't tell me there's no way to see a terminal at boot??)

---

### Post by mikewhatever on 2007-01-30
This is just a guess, but shouldn't it be Ctrl+Alt+F1? It work when the GUI is running, but I've never tried it on boot up.

Wait, try this one [http://www.ubuntuforums.org/showthread.php?t=187177](http://www.ubuntuforums.org/showthread.php?t=187177)

---

### Post by Auria on 2007-01-30
Ctrl-Alt-F1 doesn't work :/

About the guide you pointed me too - It assumes you use GRUB. I'm on PPC so i'm using Yaboot, it doesn't apply...

i feel like Ubuntu PPC should be marked unusable exeprimental stuff... right now it's just plainly ** nothing works and no one knows how to help**...

---

### Post by mikewhatever on 2007-01-30
So, you don't have the recovery mode option in Yaboot?

---

### Post by rocknrolf77 on 2007-01-30
[http://www.google.com/linux?hl=no&q=Yaboot&btnG=S%C3%B8k&lr=](http://www.google.com/linux?hl=no&q=Yaboot&btnG=S%C3%B8k&lr=)

---

### Post by Auria on 2007-01-30
I used Google... this is what i found:

> No way that I know of to get a rescue/recovery mode from the yaboot menu.
So it's looking kinda desperate...

Is there a way, from the live CD, to reconfigure the X config from my hard disk?

---

### Post by mikewhatever on 2007-01-30
Does this help? [http://www.debian.org/ports/powerpc/inst/yaboot-howto/ch9.en.html](http://www.debian.org/ports/powerpc/inst/yaboot-howto/ch9.en.html)

---

### Post by Auria on 2007-01-30
> **mikewhatever said:**
> Does this help? [http://www.debian.org/ports/powerpc/inst/yaboot-howto/ch9.en.html](http://www.debian.org/ports/powerpc/inst/yaboot-howto/ch9.en.html)

Actually i had already seen this page - it helps you if yaboot gets messed up, but doesn't help with X

HOWEVER - i got it fixed! Just as information - i installed ext2fsx, this is a mac extension to edit ext partitions, and so i was able to edit and modify xorg.conf from the mac side. Fortunately ubuntu wasn't my only system! I think a rescue mode should definitely be a must-have addition to ubuntu PPC (or Ubuntu at all, to not rely on boot manager features)

---

### Post by mikewhatever on 2007-01-30
Congratulations!

---

