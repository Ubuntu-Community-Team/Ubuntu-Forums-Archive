---
title: "sound/video is not sync"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by Fornie on 2006-06-07
i'm trying to play .avi files on my computer using totem/mplayer but i notice that sound/video is not sync...

any tips on how to resolve this? thanks ](*,) :confused:

---

### Post by Fornie on 2006-06-07
any ideas? help? please ](*,)

---

### Post by jive_turkey on 2006-06-07
I've been messing with ubuntu for a while, and I've never got totem to work the way I wanted to. Try VLC its great, its lightweight, simple and quick. I know its not a fix to your issue with totem, but its a decent workaround if your desperate for an immediate solution.

---

### Post by uzi09 on 2006-06-07
hmm, not too sure, perhaps you're missing some codecs or it wasn't a proper install. if you'd like, you can try to reinstall it using BUMPS ([http://www.ubuntuforums.org/showthread.php?t=138889)](http://www.ubuntuforums.org/showthread.php?t=138889)).

---

### Post by Fornie on 2006-06-07
thanks guys! *hands down* i'll try this later...i want to go home already....

---

### Post by BoyOfDestiny on 2006-06-08
[QUOTE=Fornie]thanks guys! *hands down* i'll try this later...i want to go home already....[/QUOTE]

It might be ESD. Try doing from a terminal (Applications -> Accessories -> Terminal) 
sudo killall esd

see if that solves it. If so, you can disable esd from System -> Preferences -> Sound
uncheck enable ESD.

Anyway, ESD has given me trouble on every ubuntu box I've setup / helped set up... Hopefully this solves your problem.

---

