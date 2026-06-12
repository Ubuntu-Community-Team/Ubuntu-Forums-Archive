---
title: "Problem updating feisty"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by hrolfp on 2007-11-14
I'm trying to update feisty before I upgrade to gutsy. I keep getting this error message:

[[IMG]http://img249.imageshack.us/img249/3986/upgradext5.th.png[/IMG]](http://img249.imageshack.us/my.php?image=upgradext5.png)

Any idea how to fix this?

---

### Post by Dr Small on 2007-11-14
```
sudo dpkg --configure -a
```

---

### Post by Inxsible on 2007-11-14
[LEFT]Open up a terminal and run```
sudo dpkg --configure -a
```
[/LEFT]

---

### Post by hrolfp on 2007-11-14
thanks!

---

### Post by hrolfp on 2007-11-14
I'm having another problem - I don't see any option to upgrade to gutsy in my update manager.

---

### Post by Inxsible on 2007-11-14
> **hrolfp said:**
> I'm having another problem - I don't see any option to upgrade to gutsy in my update manager.
try this. it may or may not work
```
sudo aptitude update && sudo aptitude upgrade
```After that manually start your update manager```
update-manager
```

---

### Post by NightCrawler03X on 2007-11-14
You shouldn't have needed us to tell you.

What you were told by the post above me is the exact instruction given by the error message.

No wonder people have problems with Linux sometimes, they can't read! :)

No offense by the way, I'm just nitpicking because I'm bored.

---

### Post by hrolfp on 2007-11-14
> **Inxsible said:**
> try this. it may or may not work
```
sudo aptitude update && sudo aptitude upgrade
```After that manually start your update manager```
update-manager
```

That didn't work.

---

### Post by Inxsible on 2007-11-14
you can either wait until it appears or simply do a fresh install, which is much better anyway.

you can make another partition and install Gutsy in there or over-write the exsting Feisty install. But if something goes wrong, then you won't be able to access the ubuntu OS in case you choose the second option.

---

