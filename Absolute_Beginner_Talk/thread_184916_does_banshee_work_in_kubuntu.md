---
title: "does banshee work in kubuntu?"
date: 2006-05-30
forum: Absolute Beginner Talk
---

### Post by mrvgarg on 2006-05-30
does banshee work in kubuntu?

---

### Post by gingermark on 2006-05-30
All Gtk apps should work in Kubuntu. Might not look too pretty though, although there is the "Gtk styles & fonts" dialog in Kcontrol / System Settings that should help in that respect.

---

### Post by aysiu on 2006-05-30
Yes, it works.

And Gingermark is right.

---

### Post by mrvgarg on 2006-05-30
Hmmm

I tried installing by

aptitude install banshee 

but it did not work so i tried sudo apt-install banshee and still did not install.](*,) ](*,) :-k

---

### Post by aysiu on 2006-05-30
Do you have [the Universe repositories enabled](http://www.psychocats.net/ubuntu/sources)?

Make sure they are and then ```
sudo aptitude update
sudo aptitude install banshee
```

---

