---
title: "dual boot question"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by bbrff on 2007-11-17
Ive recently installed Ubuntu 7.1 to my desktop with a dual boot to windows xp (my kids will kill me if I touched their msn messenger). Anyhow, I'm really enjoying ubuntu but unfortunately I tried upgrading to ubuntu studio and now things arent working so well :( I've downloaded the ubuntu studio CD and want to do a fresh install. I was wondering how this will affect the dual boot screen. I would like to have a screen that just shows the two alternatives and not the previous install. Is this possible? Thanks in advance

---

### Post by daimaru on 2007-11-17
you can always edit your /boot/grub/menu.lst file and include or delete entries that should show up during boot.
edit:#
but if you do a fresh install of ubuntu studio grub will be rewritten anyways (if you install it on same partition as ubuntu was) so there should be no menu item for previous install in grub. otherwise do the above and edit menu.lst delete prev entries.

---

### Post by bbrff on 2007-11-17
thanks ,, Im going to try a clean install. I just didn't want any problems with the dual boot because as i said, my kids will kill me if MSN goes down. Btw ,,once I get Ubuntu purrrrring the way I like, whats the best equivalent to MSN messenger that they could use that would get them interseted in Ubuntu

---

### Post by gn2 on 2007-11-17
> **bbrff said:**
> thanks ,, Im going to try a clean install. I just didn't want any problems with the dual boot because as i said, my kids will kill me if MSN goes down. Btw ,,once I get Ubuntu purrrrring the way I like, whats the best equivalent to MSN messenger that they could use that would get them interseted in Ubuntu

According to my 14 year old son, Gaim works perfectly.

I believe it's been replaced by Pidgin in 7.10 but should be available in the repos.

---

### Post by saj0577 on 2007-11-17
Pidgin is quite good are you talking about Msn Live Messenger if so their is an application in kubuntu that is very similar which they would like but i cant remember its name right now. If your interested in seeing what the programs look and feel like private message me and i will show you through vnc if you wish,

Saj

---

