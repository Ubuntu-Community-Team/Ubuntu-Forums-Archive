---
title: "[SOLVED] Kubuntu Gutsy: ATI driver problems, giant fonts"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by aks44 on 2007-10-21
So I ran Kubuntu 7.10 Live CD, and I must say I'm pretty baffled...


Whenever I use either radeon of fglrx drivers, I end up with giant fonts that basically render the comp unuseable (it can fit like 10 lines of text on 1600x1280).

The only way I managed to have a useable display is booting into safe graphics mode, which uses Vesa drivers.

On Feisty I use the radeon driver which work just fine (even AIGLX works perfectly) so I'm pretty surprised by this behaviour. My card is an ATI Radeon 9600.


I'm kind of a Linux newbie (used Kubuntu for like 6 months) and I hardly had any issues with Feisty, so I'm quite lost as of what I should do to make it work correctly. For Feisty, it has been as simple as setting the radeon driver in xorg.conf and selecting my monitor in the system settings.

Any ideas?

---

### Post by Pumalite on 2007-10-21
You might want to use ENVY: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by aks44 on 2007-10-21
Thanks for the suggestion, but IIRC Envy installs the proprietary drivers, which are slow as hell on my card when it comes to 3D (plus they don't support AIGLX).
And the radeon open source driver works just fine on Feisty, so I can't see why Gutsy can't handle it correctly?


EDIT: FWIW I noticed that Gutsy's splash screen is waaay pixelated, while I don't have this issue with Feisty's live CD. Not sure if this info is useful though, but maybe it's a kernel issue since it pops in before X? Just a wild guess...

---

### Post by aks44 on 2007-10-21
* bump *

---

### Post by aks44 on 2007-10-21
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/libgnome/+bug/118745](https://bugs.launchpad.net/ubuntu/+source/libgnome/+bug/118745) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				FWIW I'm slowly tracking this bugger down. Looks related to [this bug]("https://bugs.launchpad.net/ubuntu/+source/libgnome/+bug/118745") (X detecting bad DPI settings).

Hope this can help someone, I'll post more if/when I manage to fix it.

---

### Post by aks44 on 2007-10-22
To whom it may concern... I managed to fix the problem using [this]("https://bugs.launchpad.net/ubuntu/+source/libgnome/+bug/118745/comments/22") tip (more [here]("https://bugs.launchpad.net/ubuntu/+source/libgnome/+bug/118745/comments/71")).

---

