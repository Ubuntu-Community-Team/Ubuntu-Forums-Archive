---
title: "trouble with compiz and awn, please help"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by adreamer on 2007-11-16
i'm using ubuntu 7.10 on an intel celeron 2,6 256 DDram with an S3 Pro Savage8 integrated graphics card and i'm having trouble with both compiz and consequently avant window navigator. i managed to install awn but when i run it, it seems to open and close a fraction of a second later.
concerning compiz, i believe that to activate you need to go to System -> Preferences -> GL Desktop -> Enable GL Desktop. I do this and compiz still doesn't work.
Also in System -> Appearance -> Visual Effects, i can't activate any of the effects (normal or extra)
Is it because of the graphics card ?

---

### Post by Sims2789 on 2007-11-16
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/xorg-server/+bug/111257](https://bugs.launchpad.net/xorg-server/+bug/111257) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **adreamer said:**
> i'm using ubuntu 7.10 on an intel celeron 2,6 256 DDram with an S3 Pro Savage8 integrated graphics card and i'm having trouble with both compiz and consequently avant window navigator. i managed to install awn but when i run it, it seems to open and close a fraction of a second later.
concerning compiz, i believe that to activate you need to go to System -> Preferences -> GL Desktop -> Enable GL Desktop. I do this and compiz still doesn't work.
Also in System -> Appearance -> Visual Effects, i can't activate any of the effects (normal or extra)
Is it because of the graphics card ?

Compiz is buggy on Intel cards, especially with videos. At least it runs on them, unlike Aero with advanced affects...

---

### Post by DutyDuty on 2007-11-16
Try ```
compiz --replace &
``` in terminal.

---

