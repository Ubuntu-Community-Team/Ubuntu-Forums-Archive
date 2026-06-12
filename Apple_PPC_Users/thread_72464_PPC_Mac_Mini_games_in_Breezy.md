---
title: "PPC Mac Mini games in Breezy"
date: 2005-10-06
forum: Apple PPC Users
---

### Post by kingc8 on 2005-10-06
The follow list of games will reset your X session on PPC Mac Mini;
airstrike
battle ball
enigma
fillets-ng
holotz-castle
metal blob solid
pachi
pipenightdreams
supertux
among others.
My question is, do I file each of these as single bugs in Malone or should I report this bag of broken software as one?
The hip thing about the Debian process was that this didn't happen. On the other hand it took a million years for the last Stable of Debian.
Love,
Cameron

---

### Post by stuporglue on 2005-10-07
If all those games cause the problem, then it's probably not the games themselves. There's probably a comon denominator across all of those games that's causing the crash. If you can track down the cause, that'd be the most valuable thing to file. With so many programs having problems, I doubt they all just happen to have the same bug that does the same thing! :-)

Likely places to start would be to check if all the games use the same graphics type (SDL, OpenGL...) or sound types (Midi, mp3, ogg...). Check dmesg, note the CPU usage and available memory when they die, and check the xorg log for any clues.

I'm not a dev, but that's what I would do.

---

### Post by ssam on 2005-10-08
have you turned on composite?
do you still have problems if you run the games with a different window manager?
what graphics card do you have?

---

### Post by kingc8 on 2005-10-08
"There's probably a comon denominator across all of those games.."

:-) That sounds sensible.

I think SDL is causing the grief.

My machine is a Mac Mini 1.42Ghz 1GB ram with ATI 9250 32MB ram. OpenGL works fine, sound is fine.

So, SDL.

---

