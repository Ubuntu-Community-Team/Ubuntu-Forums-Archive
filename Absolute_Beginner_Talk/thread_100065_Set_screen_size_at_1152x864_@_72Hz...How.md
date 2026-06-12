---
title: "Set screen size at 1152x864 @ 72Hz...How?"
date: 2005-12-06
forum: Absolute Beginner Talk
---

### Post by Aiden on 2005-12-06
How can I set this?
I have a AMD Athlon 3200+ @ 2.2GHz
1GB DDR
nVidia GeForce FX5700LE (using drivers from Synaptic)

Also, is there any good WinAmp type programs? Mainly ones that allow web streaming? XMMS doesnt seem to work well with [www.hitzradio.com](www.hitzradio.com)

Also, how can I enable 5.1 or have stereo go out all speakers instead of just two? (I have a 5.1 setup).

Not a newbie to linux, but a first using it at home for leisure / work.

---

### Post by aysiu on 2005-12-06
I don't know much about sound, but [this](http://ubuntuforums.org/showpost.php?p=129379&postcount=21) has all the tips and tricks for configuring screen resolution.

---

### Post by timsch75 on 2005-12-07
make sure that the HorizSync and VertRefresh values in xorg.conf are correct for your monitor.  I couldn't get my resolution high enough when I installed ubuntu a couple of days ago.  It put in some generic values which were nowhere close to correct, severely limiting the resolution options.  Also, if you still have problems, try removing all resolution options other than the one you want in xorg.conf

---

