---
title: "[SOLVED] All media players turn movies pink -- reboot to fix"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by altonbr on 2007-12-06
No matter what media player I use (gxine, vlc, mplayer, totem) or what file format the movie is in (wmv, avi, mpeg), my movies seem to 'randomly' turn pink and I have to reboot to fix the codecs.

Is this a codec problem or a Compiz problem?

I've attached a screen.

Many thanks!

---

### Post by dfreer on 2007-12-06
I seem to have this problem happen as well, using an nvidia geforce 7400.

It seems to only occur when using Compiz Fusion, it'll run fine for awhile with compiz, but once the movies start glitching up, only restarting the X server seems to fix it. Switching back to metacity **after** the glitch occurs does not help.

---

### Post by jba6511 on 2007-12-06
it is a known bug in the nvidia drivers. 

[http://ubuntuforums.org/showthread.php?t=572057](http://ubuntuforums.org/showthread.php?t=572057)

---

### Post by lvleph on 2007-12-06
> **jba6511 said:**
> it is a known bug in the nvidia drivers. 

[http://ubuntuforums.org/showthread.php?t=572057](http://ubuntuforums.org/showthread.php?t=572057)

And that is what people keep saying, but I do not have an nvidia card and I still have the same problem. I have recompiled my kernel with SLAB instead of SLUB. This seems to have addressed the issue, but I think it is too early for me to say it is fixed.

---

### Post by altonbr on 2007-12-06
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/146455](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/146455) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **jba6511 said:**
> it is a known bug in the nvidia drivers. 

[http://ubuntuforums.org/showthread.php?t=572057](http://ubuntuforums.org/showthread.php?t=572057)

Thanks, I ended up posting my problem here: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/146455](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/146455).

---

