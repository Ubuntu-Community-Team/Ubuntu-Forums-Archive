---
title: "Stream iTunes to Linux"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by nhandler on 2007-04-14
iTunes is capable of sharing its library to multiple computers that have iTunes installed. Is there any way to trick iTunes into streaming the music to Ubuntu?

---

### Post by chalex on 2007-04-14
it should certainly be possible.  iTunes uses "Rendezvous" which is the same thing as "Zeroconf" which is handled by the avahi program in Ubuntu.  I think it's part of the default install.  Look in the help files for Rhythmbox or whatever music player you use.

---

### Post by nhandler on 2007-04-14
Rhythmbox shows the name of the shared iTunes library in the panel on the left. However, nothing happens when I click it. I couldn't figure out how to connect in amarok.

---

### Post by doclivingston on 2007-04-16
Is this with iTunes 7? If so, you're out of luck - Apple delibrately broke compatibility with all other players (including iTunes 6) when they released iTunes 7, and no-one has figured out the new "hash" algorithm it uses.

---

### Post by nhandler on 2007-04-16
Ok, so that won't work. One last question, is it possible to have itunes 6 and itunes 7 running on the same computer? The reason I ask is that if it is, I could keep itunes 6 around to stream music, and use itunes 7 for my ipod.

---

