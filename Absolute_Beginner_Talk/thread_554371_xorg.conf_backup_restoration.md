---
title: "xorg.conf backup restoration?"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by kevin11951 on 2007-09-18
pretty much everyone is telling you how to backup the xorg.conf file when editing it, but no one tells you how to RESTORE the file if you do mess up the original!?

---

### Post by kelnage on 2007-09-18
Basically, you do the same command again, but this time you reverse the parameters.

So, I imagine originally it was something like this:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

So to restore, you do:

```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```

---

### Post by kevin11951 on 2007-09-18
oh... that easy, now i sound like an idiot!

---

### Post by irish_flu on 2007-09-18
No problem, you'll be restoring yours in no time.

All you need to do is change the name of your backup file to xorg.conf and you're on your way.

Of course, it's good practice to keep the broken one, too (just in case something you don't know about is screwed up).

So how I'd do it is this:
sudo mv xorg.conf xorg.conf.broken
sudo cp xorg.conf.backup xorg.conf

"cp" is copy and "mv" is "move".  Of course, replace "xnord.conf.backup" with whatever you named your backup file.

Helpful?  If not, holler!

EDIT: Hoo-hah, beaten to the punch!

---

### Post by kevin11951 on 2007-09-18
thanks, all of you for your help, very fast response! (and no one called me an idiot, unlike in the linux forums!)

---

