---
title: "Why won't my scripts run when I log on?"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by Yes on 2008-02-08
If you just add 'conky' to your startup sessions when using Compiz, Conky won't display right.  So you need to have Conky wait a few seconds before starting.  I tried putting 'sleep 10 && conky' in sessions, but Conky won't start.  I tried putting that into a bash file and adding that to sessions, but that doesn't work.  I even put the commands in an alias and added the alias to sessions, but Conky still won't start.  All of those methods start Conky when I try running them from the terminal, why don't they run when they're in sessions?

Thanks.

---

### Post by dcstar on 2008-02-09
> **Yes said:**
> If you just add 'conky' to your startup sessions when using Compiz, Conky won't display right.  So you need to have Conky wait a few seconds before starting.  I tried putting 'sleep 10 && conky' in sessions, but Conky won't start.  I tried putting that into a bash file and adding that to sessions, but that doesn't work.  I even put the commands in an alias and added the alias to sessions, but Conky still won't start.  All of those methods start Conky when I try running them from the terminal, why don't they run when they're in sessions?

Thanks.

Because a terminal has its own environment, which is different when things are run in other places.

---

### Post by jordanmthomas on 2008-02-09
I used to have this problem with conky.  If I started it before compiz, it would only come up on one desktop.  It recently started to work this way though.

What version of conky are you using?  I'm using 1.4.9 and this problem doesn't seem to be around for me any more.  I don't use gnome, and just have conky, pypanel, and compiz run from my .xinitrc, but the same principles should apply for gnome I'd think.

If you don't have 1.4.9, try upgrading to it and see if you are able to run conky before compiz.

---

### Post by spiderbatdad on 2008-02-09
you could make a panel launcher for conky. i realize you may not want to click a launcher to start it, but...
also, what about setting start order to 99...i haven't had much luck with the quirky sessions manager.

---

