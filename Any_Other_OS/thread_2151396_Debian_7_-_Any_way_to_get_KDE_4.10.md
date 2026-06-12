---
title: "Debian 7 - Any way to get KDE 4.10?"
date: 2013-06-04
forum: Any Other OS
---

### Post by Roasted on 2013-06-04
Pretty much as the title says. Just curious if there's a way to get KDE 4.10 on Debian 7 without having to dismantle the entire system and compile everything for a few hours. Any ideas?

---

### Post by mips on 2013-06-04
[http://crunchbang.org/forums/viewtopic.php?pid=248917%23p248917](http://crunchbang.org/forums/viewtopic.php?pid=248917%23p248917) I've used this before.

[http://vsido.org/index.php?topic=280.0](http://vsido.org/index.php?topic=280.0)
[https://sites.google.com/site/debianinstallnotes/tutorial/xfce/xfce-4-10](https://sites.google.com/site/debianinstallnotes/tutorial/xfce/xfce-4-10)

---

### Post by Roasted on 2013-06-04
> **mips said:**
> [http://crunchbang.org/forums/viewtopic.php?pid=248917%23p248917](http://crunchbang.org/forums/viewtopic.php?pid=248917%23p248917) I've used this before.

[http://vsido.org/index.php?topic=280.0](http://vsido.org/index.php?topic=280.0)
[https://sites.google.com/site/debianinstallnotes/tutorial/xfce/xfce-4-10](https://sites.google.com/site/debianinstallnotes/tutorial/xfce/xfce-4-10)

Am I missing something, or did you link the wrong DE? :P

---

### Post by mips on 2013-06-04
> **Roasted said:**
> Am I missing something, or did you link the wrong DE? :P

:redface::oops: Yeah, I have no idea how I read KDE as XFCE, my mind must be elsewhere, sorry about that.

---

### Post by mips on 2013-06-04
SolydXK seems to be based on Wheezy so maybe this might work for you [http://forums.solydxk.com/viewtopic.php?f=9&t=431&start=20](http://forums.solydxk.com/viewtopic.php?f=9&t=431&start=20)

---

### Post by Roasted on 2013-06-05
Part of my goal behind getting to KDE 4.10 was largely to use the Homerun Launcher with it. Does anybody know if it's somehow installable on KDE 4.8?

---

### Post by T.J. on 2013-06-05
With respect Roasted, if you are using Debian 7.0 (stable), then before you install KDE 4.10 on it, you may want to consider that doing it improperly can break your package manager data, possibly beyond the average user to recover.  KDE 4.10 has been tested upstream, but not against the current version of Debian 7's 36,000+ packages.  KDE 4.10 has been available for only 3-4 months.  If you really want to play with new and probably a little buggy versions of the software, I'd just install Kubuntu 12.04 or 13.04 and save yourself a lot of time and trouble.  (My experiences with 13.04 have been less than optimal - sadly.) Another possibility is that you could try Debian Testing or the Debian Unstable trees, although you should check to make sure that they have the versions that you want.

Have you tried pulling the source for the Homerun applet from the Kubuntu repository and compiling it against the the Debian 7 KDE libs?  You've made me curious.  If I try it I'll let you know.

---

### Post by T.J. on 2013-06-05
I tried to compile it against Debian 7, which uses 4.8.  Unfortunately, it did not work. 

*"ERROR: the installed kdelibs version 4.8.4 is too old, at least version 4.9.97 is required"*

I'd just install Ubuntu 12.04 as it is more stable than 13.04.  The Kubuntu project has packages for it.  If you want to compile KDE 4.10 by hand, then by all means - but Kubuntu will save you some time and work.  Since Debian's package collection is the source for Ubuntu's then I doubt you will be missing anything you might need.  Either compiling KDE yourself or using Ubuntu - it's the same result.

---

### Post by eric71 on 2013-06-07
I think ZevonOS Neptune is a way to go for getting KDE 4.10 on a Wheezy base. Haven't tried the latest versions, but I have liked it in the past.

[http://www.zevenos.com/download/zevenos-neptune-2](http://www.zevenos.com/download/zevenos-neptune-2)

---

