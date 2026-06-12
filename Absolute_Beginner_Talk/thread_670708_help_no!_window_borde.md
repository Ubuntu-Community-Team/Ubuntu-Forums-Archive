---
title: "help no! window borde"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by exneo002 on 2008-01-17
MY bro canceld my fiesty to gutsy upgrade to play runescape now I have no window border in gnome help

---

### Post by nikoPSK on 2008-01-17
screenshot appreciated. Do you run compiz? If so, make sure the window decoration plugin is enabled. If you can't really fix, reinstall. It's best to lock a system when left alone updating.

---

### Post by peitschie on 2008-01-17
Mmm... a broken upgrade can be no fun at all!

Try running the following from a terminal (Accessories > Terminal):
```

see SOULRiDER's suggestion below ;)

```

Unfortunately however, recovering from an interrupted upgrade is often a touch and god affair...

Is there any possibility you could clean the computer and reinstall Gutsy?

---

### Post by SOULRiDER on 2008-01-17
I would suggets doing a dist-upgrade ither than an upgradenand using aptitude instead of apt-get
```
sudo aptitude update
sudo aptitude dist-upgrade
```

---

### Post by exneo002 on 2008-01-18
I ran upgrade but some lib packages got interupted so I need to upgrade and see cause compiz won't install because im missing these

---

### Post by SOULRiDER on 2008-01-18
Have you done ```
sudo aptitude dist-upgrade
```

Also, try running
```
sudo dpkg --configure -a
```

---

### Post by exneo002 on 2008-01-18
tried configure use wubi to slow to run I think I'll just use my backup xfce manager can it run compiz

---

