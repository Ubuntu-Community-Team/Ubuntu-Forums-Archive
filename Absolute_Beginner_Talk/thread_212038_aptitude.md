---
title: "aptitude"
date: 2006-07-09
forum: Absolute Beginner Talk
---

### Post by Drakkor on 2006-07-09
I've heard many times on the board to use aptitude instead of apt-get,
what about installing things with synaptic and dependencies ?  Thanks :o

---

### Post by FredB on 2006-07-09
I prefer apt-get, other prefer aptitude. It is a matter of taste.

Synaptic is - in a way - a graphical interface to apt-get. So it is simpler to use Synaptic which drives apt-get in its works.

Using synaptic is completely painless and sure.

---

### Post by Jucato on 2006-07-09
I usually do use apt-get, aptitude, or synaptic/adept, depending on the situation.

1. I need to install 1-3 unrelated packages fast, I use apt-get.
2. I need to install a metapackage/package with lots of dependencies, usually totalling 20 or more packages, I use aptitude.
3. I want to do #1 in a GUI, I use Synaptic/Adept.
4. I want to do #2 in a GUI, I use Synaptic, with a slight twist:
(shameless plug to my own guide...) [http://www.ubuntuforums.org/showthread.php?t=141409](http://www.ubuntuforums.org/showthread.php?t=141409)

---

### Post by aysiu on 2006-07-09
> **FredB said:**
> I prefer apt-get, other prefer aptitude. It is a matter of taste. More specifically, it's a matter of what you expect your command to do.

If you *apt-get install* to install and then expect *apt-get remove* to remove the dependencies that came with that application, forget it.

If you *apt-get install* and then *apt-get remove* and expect to remove only the application you specify for removal, then, yes, *apt-get* will be to your taste.

[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude) for more details.

---

