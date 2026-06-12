---
title: "Phantom start programs"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by swoll1980 on 2007-06-25
I switched to xubuntu because of some ram issues I was having. Everything went smooth exept for the fact that the start programs that I had set up in ubuntu are still starting up in xubuntu, and when I go to the start up programs in xubuntu the programs are not there. So ther is some other program starting these programs, but I don't know the name of this program or how to find it. Can someone help me with this please?

---

### Post by PiratePhysicist on 2007-06-25
Well, if you're really as desperate as you were making yourself sound in the other thread you started, then simply back up important files, wipe drive and start over.

---

### Post by swoll1980 on 2007-06-25
Thats not helpful at all

---

### Post by eljalill on 2007-06-25
You could check in ~/.config/autostart . Anything in there, even if not in the start-up programs dialogue will be started at start-up. Mostly the files in there are .desktop files,
so you could also check where else you have a collection of them (e.g. /etc/xgd/autostart with me) and edit them there /delete the .desktops which you don't want.

but  m a k e _ s u r e _ y o u _ h a v e _  a _  b a c k u p !!! (Sorry I I am telling you things here which you already know... better safe than sorry!)

Hope this helps

---

### Post by swoll1980 on 2007-06-25
Thats exactly what I needed to know thank you very much

---

