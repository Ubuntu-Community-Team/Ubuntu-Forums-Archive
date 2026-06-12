---
title: "wine + beryl = no window borders.  Please help."
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by laptoplinux on 2007-08-27
I've noticed that whenever I run wine applications while using beryl, the window borders do not display.  This is different from many of the other beryl window border topics I've seen in that non-wine windows display perfectly, and I've already enabled the wine-workarounds in the beryl settings manager.  What else might be the problem and how can I fix it?

---

### Post by Vadi on 2007-08-27
Upgrade to Compiz? That problem might have been fixed already but Beryl isn't being worked on anymore. You'd want to get Compiz Fusion now.

---

### Post by mysticmatrix on 2007-08-27
I am also having these errors but they have appeared only 2 days ago. Previously, wine windows ran fine.
Moreover, crossover windows still run fine.

Can anybody help?

[Really I haven't provided more precise information as I don't know what to tell. If someone points out I may provide information/]

---

### Post by laptoplinux on 2007-08-27
I tried upgrading to Compiz-Fusion about a week ago.  The upgrade went through ok, but the current state of Compiz-Fusion left my desktop an unusable mess with no way back to Beryl.  It was as if the fusion picked up all of Compiz's clunkiness without taking in any of Beryl's polish and functionality.  I was forced to reinstall Ubuntu to get things back to normal.  I'll wait a couple more releases before looking at CF again.  Oddly enough, I don't remember having the beryl + wine problem on the old Ubuntu install, so I can't figure out what is different this time.

---

### Post by sailor2001 on 2007-08-27
go to places/homefolder and click ctrl/h  scroll to sessions and click to rename.. rename as something like:  sessions.old.........ctrl/alt/backspace   a new sessions script will be written

---

### Post by zlO_Olz on 2007-08-27
> **mysticmatrix said:**
> I am also having these errors but they have appeared only 2 days ago. Previously, wine windows ran fine.]


same problem here with xubuntu...

[IMG]http://img53.imageshack.us/img53/2214/nomenubarox0.png[/IMG]

---

### Post by Vadi on 2007-08-27
Ahh there's a similar topic on the compiz forums:

[http://forum.compiz-fusion.org/showthread.php?t=3653&highlight=wine+borders](http://forum.compiz-fusion.org/showthread.php?t=3653&highlight=wine+borders)

It looks like you people are using Trevino's repository, which you need to keep in mind - features bleeding edge. Looks like one of the latest upgrades broke it.

---

### Post by mysticmatrix on 2007-08-28
> **Vadi said:**
> Ahh there's a similar topic on the compiz forums:

[http://forum.compiz-fusion.org/showthread.php?t=3653&highlight=wine+borders](http://forum.compiz-fusion.org/showthread.php?t=3653&highlight=wine+borders)

It looks like you people are using Trevino's repository, which you need to keep in mind - features bleeding edge. Looks like one of the latest upgrades broke it.

I am using Beryl from offical Feisty repo that is 0.2.0. The problem appeared only 2 days ago. Previously it was running all fine. Also I have noticed that if I reload Beryl from the little red Beryl icon in system tray, my windows do get border.

---

### Post by Vadi on 2007-08-28
Beryl relies in Compiz as it's engine, and Compiz the engine was getting the tweaks. Beryl is really just the add-on effecs that use the engine.

As for window management trouble, I had a similar issue, except with all windows. But I did something weird and not even my normal (metacity) won't show window borders, I have to load Compiz to get them. heh.

---

### Post by isecore on 2007-08-29
I'm the one who wrote the thread over on the Compiz-forums. If you read that thread you'll find one reply from someone who isn't using Trevinos repository, which to me indicates that it's not something that necessarily is isolated to his repo.

However, this is a weird bug since in my case it's only one or two applications that suffer from it. Most other apps I run through Wine run just fine.

---

### Post by MeMosh on 2007-08-29
Same problem here, this started a couple of days ago after a wine update i think.

like the others, the only way having borders back is reload  beryl with  the wine window open. :(

---

### Post by Juan_VCS on 2007-08-29
I think it might just be a wine 0.9.44 issue. I've noticed that some games that worked fine in the previous version, now run pretty slow.

---

