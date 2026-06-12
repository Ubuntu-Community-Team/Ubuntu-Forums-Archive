---
title: "[SOLVED] HP Pavilion dv9428nr -- LiveCD Fails To Load"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by companyman on 2007-08-21
[FONT="Arial"]Hi,

I have a HP Pavilion dv9428nr laptop ([specifications available here]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01062257&lc=en&cc=us&dlc=en&product=3439691&lang=en")). I can boot to the livecd menu but cannot boot any farther; I cannot successfully and completely "start or install Ubuntu" or "start Ubuntu in safe graphics mode". The CD seems to _try_ and boot farther but, eventually, hangs on a black screen -- possibly before I see the beginnings of a GUI? I'm not sure what to look for.

I've tested the "Standard personal computer (x86 architecture, PentiumTM, CeleronTM, AthlonTM, SempronTM)" and "64bit AMD and Intel computers" versions. No luck.

I'm hoping someone could look at my system specifications and make some recommendations?

Thanks![/FONT]

---

### Post by overdrank on 2007-08-21
> **companyman said:**
> [FONT="Arial"]Hi,

I have a HP Pavilion dv9428nr laptop ([specifications available here]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01062257&lc=en&cc=us&dlc=en&product=3439691&lang=en")). I can boot to the livecd menu but cannot boot any farther; I cannot successfully and completely "start or install Ubuntu" or "start Ubuntu in safe graphics mode". The CD seems to _try_ and boot farther but, eventually, hangs on a black screen -- possibly before I see the beginnings of a GUI? I'm not sure what to look for.

I've tested the "Standard personal computer (x86 architecture, PentiumTM, CeleronTM, AthlonTM, SempronTM)" and "64bit AMD and Intel computers" versions. No luck.

I'm hoping someone could look at my system specifications and make some recommendations?

Thanks![/FONT]
Hi and welcome you may look at these
[http://ubuntuforums.org/showthread.php?t=478050&highlight=NVIDIA+GeForce+Go+6150&page=2](http://ubuntuforums.org/showthread.php?t=478050&highlight=NVIDIA+GeForce+Go+6150&page=2)
[http://ubuntuforums.org/showthread.php?t=516132&highlight=NVIDIA+GeForce+Go+6150](http://ubuntuforums.org/showthread.php?t=516132&highlight=NVIDIA+GeForce+Go+6150)
Good luck!

---

### Post by jnorthr on 2007-08-21
The spec looks ok, as your machine is an amd64 you should try burning his image: [ftp://ubuntu.univ-nantes.fr/ubuntu-cd/feisty/ubuntu-7.04-desktop-amd64.iso](ftp://ubuntu.univ-nantes.fr/ubuntu-cd/feisty/ubuntu-7.04-desktop-amd64.iso) from here: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Burn it at the slowest possible speed to avoid burn errors in the image. Put cd in your machine then reboot. This should work correctly as ubuntu will run completely from the cd (and a small bit of hard drive space). If this does not work please provide a list of messages seen during reboot. Do you ever see any menus or GUI ? or does it appear to hang before reaching that point ?

---

### Post by companyman on 2007-08-21
[FONT="Arial"]Hi,

Thanks for the links!!

In reading [Keyper7's post (here)]("http://ubuntuforums.org/showpost.php?p=2871420&postcount=1"), KeyPer7 says adding "noapic noirqdebug" allowed the livecd to load Ubuntu. What would such a command do? _How_ and _where_ would I add "noapic noirqdebug"?

Thanks.[/FONT]

---

### Post by companyman on 2007-08-21
[FONT="Arial"]Hi,

Any assistance would be appreciated.

Thanks.[/FONT]

---

### Post by logos34 on 2007-08-21
> **companyman said:**
> [FONT="Arial"]Hi,

Thanks for the links!!

In reading [Keyper7's post (here)]("http://ubuntuforums.org/showpost.php?p=2871420&postcount=1"), KeyPer7 says adding "noapic noirqdebug" allowed the livecd to load Ubuntu. What would such a command do? _How_ and _where_ would I add "noapic noirqdebug"?

Thanks.[/FONT]

Press F6 and add it to end of kernel line

---

### Post by companyman on 2007-08-21
[FONT="Arial"]Hi,

That worked. Ubuntu is installed!!

Thanks.[/FONT]

---

