---
title: "monitor out of range"
date: 2009-03-14
forum: Apple Hardware Users
---

### Post by sid001 on 2009-03-14
I just installed Xubuntu 8.10 on my PPC mac. The installatio went fine and when i rebooted it went to the boot screen (yaboot 1.3.3 or something like that) and it said ( boot: loading kernel... and eventually started booting by itself. but after that

my computer screen goes black and says "Attention Out of Range H: 4.1KHz v: 109.9HZ

somehow i managed to boot xubuntu in low graphics mode but how can i modify my settings so it boots in the resolution i want it to. 

PS: I looked at some other threads... something about etc/x11/xorg.config, i went there but i can't seem to go past that... i don't know what to do after that. (i am a newbie)

Any help would be greatly appreciated
THanks

---

### Post by hictio on 2009-03-14
What is your PPC Mac? A laptop?
You need to get the values of your monitor (or LCD if a laptop) for the horizontal and vertical refresh rates, so you can add those to the configuration file you mentioned ('/etc/X11/xorg.conf') and then re-init the box, or logout and back in; to activate the changes.

Get the values first of all.

---

