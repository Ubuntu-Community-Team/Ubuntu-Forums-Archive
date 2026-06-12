---
title: "Auto Screensaver... logged in or not?"
date: 2022-01-31
forum: Apple Hardware Users
---

### Post by tobias-richards on 2022-01-31
I've Ubuntu Server with no X, no X11, no X.org, and certainly not Wayland. The dang thing is (don't judge) a 2009 iMac that I got for $100. Obviously, I cannot power off the monitor without powering off the whole thing. So, I looked into how to avoid screen burn-in...

There was a lot about a software shutdown of the screen. This works on other hardware, but unfortunately it makes the screen Mac-bootup-EFI-white on my system.

I found some great tips for console based screensavers. My favorite (after "apt install bsdgames") is "/usr/games/worms -d 190 -n 4". Second is "/usr/games/rain -d 190". Those work just fine if I invoke them manually. How do I make such a thing activate every X minutes whether or not I'm logged in, even if I have never logged in? since boot? I don't want "Login:" nor "myhost $" nor "myhost #" burned into my screen even if I forget to start the screensaver before bed.

Yes I need the damned thing on all the time. I installed BIND so that I can have private DNS behind my router. If this thing goes down then no DNS unless I use a secondary. In my experience, secondary DNS *sucks* because primary DNS must time out first.

Please help me save my console screen under every circumstance when it's idle for X minutes. Shut the screen off. Run a console screensaver. I don't care as long as I avoid burn-in (and as long as it doesn't turn pure white).

---

### Post by deadflowr on 2022-01-31
*Thread moved to **Apple Hardware Users***

---

