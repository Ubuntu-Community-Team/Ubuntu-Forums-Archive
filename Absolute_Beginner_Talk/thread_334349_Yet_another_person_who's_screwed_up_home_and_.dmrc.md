---
title: "Yet another person who's screwed up home and .dmrc permissions"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by wstrinz on 2007-01-08
Like so many other people apparently, I have screwed up ownership of my .dmrc and home permissions. I believe I did this by changing my permissions to root and my group to root, but I have tried so many different fixes by now it probably doesn&#8217;t matter what in particular started it. Anyway, I have a problem **different** from the other people who've done this; every time I run a command involving .dmrc I&#8217;m told that it doesn&#8217;t exist. Currently, to fix this, I've tried:

Resetting home permissions to 755
Bodhi zazens 2 fixes
Various attempts of my own which have probably made it worse

again, any attempt to check .dmrc permissions fails because it says it doesn't exist.

Sorry for breaking my computer, and messing around with sudo when dont know what I'm doing, promise i wont do it again (thats probably not true, but anyway?).

Anyone know what else i can do?

Edit: I've also gone in (through a different account and checked my /home/wstrinz folder with ls -la. There's no .dmrc file)
Edit 2: Ha, may have found out why it's missing; Bodhi Zazen's fix involves removing it at the end. Apparently it wasnt recreated... how do i fix this?

---

