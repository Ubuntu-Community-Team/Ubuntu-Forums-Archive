---
title: "X Server Crashes with SIGSEGV when firefox starts"
date: 2012-07-18
forum: Any Other OS
---

### Post by alliphant on 2012-07-18
Hi everyone,

OK, this bug is livable with but very very annoying. I /am/ running Linux Mint, but it's based on Ubuntu and I think ubuntu users may have this problem too. Please help me if you can!!

Reproducable: not always.
a) start system.
b) load firefox.
c) profilemanager comes up (by default on my computer); select profile. CRASH.

Symptoms (one of these will happen; b) only happens on the boot up after a) happened, but is much rarer).
a) Screen freezes. No buttons have any effect, not Ctrl+Alt+Backspace, power, nothing. There is a high-pitched wine, possibly from my monitor but probably from something else. The only thing I can do is hold down power and do a hard reset.
b) Screen goes black and then the login prompt is shown.

Cause: Well...
a) I had a look in my /var/log/Xorg.log.0.old file when this happened once (after much googling), and found something about a SIGSEGV (segmentation fault?). Unfortunately I didn't save the file, and it doesn't have it any more.

This used to happen about 50% of the time when I started firefox. The frequency is less now, but it can now happen at any time while firefox is loaded. It started after an update, which I think may have included libcairo but I honestly didn't look.

All I've found out about this is that it might be something to do with the interaction between firefox, X server and an updated version of libcairo. apt-get won't let me downgrade (no alternative versions listed) libcairo, and downloading and installing it went wrong somehow (think it went into the wrong directory).

Has anyone else had this or has an idea on how to fix it? I am experienced with Linux (ish), I'll run any commands/get any info you need. I'm very stumped :(

OS: Linux Mint 12 (based on 11.04 ubuntu)
Graphics: AMD Radeon (I know, but I thought i was past all those driver issues...)

---

### Post by alliphant on 2012-07-18
Posted on mint forums: [http://forums.linuxmint.com/viewtopic.php?f=47&t=107958](http://forums.linuxmint.com/viewtopic.php?f=47&t=107958)

---

### Post by Perfect Storm on 2012-07-19
Moved to Other OS/Distro Talk.

---

### Post by alliphant on 2012-07-19
Thank you, mystery AI admin person :P

In other news, this happens with either of my profiles with or without safe mode. I've been trying to find a log file to look at, but can't seem to find any, and in any case it's as if everything freezes very suddenly so I don't know if anything would have a chance to write anything.

---

