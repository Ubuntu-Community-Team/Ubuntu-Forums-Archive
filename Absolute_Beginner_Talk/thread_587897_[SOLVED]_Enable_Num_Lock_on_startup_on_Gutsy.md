---
title: "[SOLVED] Enable Num Lock on startup on Gutsy"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by qprfact on 2007-10-23
With Feisty, this was documented in [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_turn_on_Num_Lock_on_GNOME_startup](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_turn_on_Num_Lock_on_GNOME_startup)

But in Gutsy the file it refers to (/etc/X11/gdm/Init/Default) doesn't exist!

What do I need to do to make this work please?

Thanks!

---

### Post by FredB on 2007-10-23
```
sudo aptitude install numlockx
```

It could make the trick.

---

### Post by ericartman on 2007-10-23
This thread helped me
[http://ubuntuforums.org/showthread.php?p=3108250](http://ubuntuforums.org/showthread.php?p=3108250)


Cart

---

### Post by Sef on 2007-10-23
To get it to work, the first time I have to push the numlock button.  After that, it comes on upon boot.

---

### Post by drs305 on 2007-10-23
,,, what Sef said.

I have a checklist of things to install when I change to a new version of ubuntu. One was to install numlockx and put it in my startup sessions. As qprfact found, there is no /etc/X11/gdm/Init/Default in Gutsy.

I've experimented and found that I could remove numlockx (or not install it at all) and if I had numlock ON when I shut down the computer the first time it automatically was ON after reboot. This is probably one of the improvements of Gutsy.

---

### Post by qprfact on 2007-10-23
I removed numlockx and found that NumLock indeed stayed on. A little disorientating, as the light didn't stay on as it did in Feisty, but it did work!

Thanks

---

### Post by qprfact on 2007-11-03
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Enabling_NUM_LOCK_at_boot](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Enabling_NUM_LOCK_at_boot)

---

