---
title: "VMPlayer Runs Painfully Slow after Idling"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by AViewAnew on 2007-02-27
I suppose this isn't absolute beginner stuff, but I didn't know where else to put it.

I'm running Edgy, with a 4400+ 64 bit AMD and 4 GB of RAM.  I have Windows XP (32 bit) running in VMPlayer.

After I've left VMPlayer idle for a bit, an hour, sometimes less, it lags like hell.  Clicking something takes forever, closing a program takes forever, sometimes even typing takes a while for the letters to appear, etc etc.  It's a really clean install of Windows - it has Visual C++ Express, Tortoise SVN, MySQL, and Firefox and that's it.  No popups, nothing like that.  It's been given 2 GB of RAM.

I suspect it's Edgy that is killing it's performance - Firefox 1.5 on Windows used to page itself out of memory, so if you left it minimized for a while and then went back to it, it took forever to maximize.  I was thinking it was something like that.

I tried sudo nice -15 vmplayer but it was the same symptom, no improvement.

---

