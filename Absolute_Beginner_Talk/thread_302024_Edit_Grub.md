---
title: "Edit Grub"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by gentlemanmasher on 2006-11-18
I want to take off some of my option's on boot.  How can I take some of these off.  I think they were one's I made for backup.  I have around 8 choices.

---

### Post by taurus on 2006-11-18
Open a terminal, Applications -> Accessories -> Terminal, and type

```
gksudo gedit /boot/grub/menu.lst
```
p.s.  Just be real careful what you remove from the list...

---

### Post by almahtar on 2006-11-18
Yes, do.  It's pretty straight forward but if you have any questions don't hesitate to post here before taking action.  Messing up your menu.lst will mean your system won't boot.  Fixing that would mean booting up into a live CD and going through some trouble.

---

### Post by gentlemanmasher on 2006-11-18
Worked great.  took off the ones I wanted it too.

---

### Post by CatKiller on 2006-11-18
If a lot of the options were to do with old kernels that you don't use any more, it's also possible to remove those packages with Synaptic.

---

