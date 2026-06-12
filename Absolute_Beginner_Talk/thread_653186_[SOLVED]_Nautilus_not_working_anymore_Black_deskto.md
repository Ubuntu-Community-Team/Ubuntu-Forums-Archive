---
title: "[SOLVED] Nautilus not working anymore Black desktop bug...http://apt.schmidtke-hb.de"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by daimaru on 2007-12-29
this problem popped up today for me so it must have been in the recent updates i preformed through aptitude. I still can't believe that this new not working libbeagle was released with the updates. I did not add [http://apt.schmidtke-hb.de](http://apt.schmidtke-hb.de) to my apt sources (at least i can not recall ever adding that url) but it showed up there today and i guess libbeagle got updated from there. 

As i turned on my computer nautilus was not working so i had a black desktop now home folder stuff etc (guess it got broken at update yesterday or maybe this morning). 

[COLOR=Red]Fix:[/COLOR]
removed [http://apt.schmidtke-hb.de](http://apt.schmidtke-hb.de) from sources, update sources, removed and then reinstall libbeagle, nautilus and ubuntu-desktop packages. 
**After doing this i found this** [thread]("http://ubuntuforums.org/showthread.php?t=652477&highlight=libbeagle") where Gigamo uses a more elegant way to fix it. In Synaptic search for libbeagle click > Package -> Force Version and selected the default (gutsy) version. It then downgraded...just in case anyone has the same problem thats how you solve it. 

I still don't get why an update is released that totally kills your workstation if you don't know enough to fix it... :confused:

---

### Post by clayt0njknight on 2007-12-29
Had the same (or similar rather) problem here...  but with Compiz.  Silly me, installed xserver-xgl and had a perfectly good version of compiz running.  ran updates, i get a black desktop upon login with no window borders.  low and behold, there was a new compiz update!  which meant simply unblacklisting my intel x3100 series card but still  it took me a few minutes to think that one through.

---

