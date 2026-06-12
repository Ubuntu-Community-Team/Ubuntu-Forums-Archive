---
title: "upgrading possibly  ubuntu repositories"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by QUEEN HIPPOLYTA on 2006-11-08
I am considering upgrading to edgy and am wondering once I do this what changes I need to make to the repositories so that I am not getting outdated software not meant for my system.

---

### Post by an.echte.trilingue on 2006-11-08
just edit /etc/apt/sources.list and change every instance of your old version to "edgy"... or did you have specific 3rd party repositories in mind?

---

### Post by QUEEN HIPPOLYTA on 2006-11-08
No I just was wondering how to do it since I am new to Ubuntu, also I did try upgrading and while everything seemed to work ok in 6.10 the boot screen would freeze on me when powering down or restarting my pc is this a known issue? If so how do you fix it. The only thing I was able to do was  power down my pc manually.

---

### Post by an.echte.trilingue on 2006-11-08
Well, just be sure that you have read [this page]("https://help.ubuntu.com/community/UpgradeNotes") and follexed its instructions.  Secondly, for your freeze, what step does it freeze on?

---

### Post by QUEEN HIPPOLYTA on 2006-11-08
in 6.10 it freezes on the boot screen when it is logging off thus forcing me to manually power down my  computer by hitting the power button, and is slow to start up on the boot screen once it has started all seems to work just fine.

---

### Post by an.echte.trilingue on 2006-11-08
Let me be more specific.  If you get to the screen with the progress bar, hit "esc" or "F2" right away to watch the system messages.  Take note of the last thing it says or of anything that is says fails.  We will try to work from there for starters.

Just to make sure, this only happens when you are turning the computer off and not when you just "log out" to get to the log in screen, right?

I will be on line for about another two hours to help you.

Good luck! 
-mat

---

### Post by QUEEN HIPPOLYTA on 2006-11-08
Actually, it happens on 6.10 if I try to restart or shutdown the system. Perhaps I better off staying at 6.06 but I really would love to upgrade to 6.10

---

### Post by an.echte.trilingue on 2006-11-08
My general feeling on upgrades is that you should never upgrade a system that works unless you actually have a reason to.  Most of the new things in edgy (the new firefox or the new GNOME, for example) will be ported to breezy.  You have very little to gain and a lot to lose: you will have to fix new bugs, redo configs, etc.  It is hard not to get caught in the "latest and greatest" craze, but let's be honest, unless you have a new computer, you probably won't get anything other than new artwork out of an upgrade.  It's not worth the headache, unless you actually enjoy fixing stuff over using your computer to do things.

Just my €0.02

---

