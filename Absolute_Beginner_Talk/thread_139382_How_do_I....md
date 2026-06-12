---
title: "How do I..."
date: 2006-03-03
forum: Absolute Beginner Talk
---

### Post by qwazert on 2006-03-03
...get rid of "programs" that I no longer want?

I'm not impressed with the performance of the KDE Desktop, Fluxbox crashed when started, and there's a few other "little ones" that I don't use or want anymore.

sudo apt-get remove *"name of app"* or uninstall?

---

### Post by Resurrection on 2006-03-03
Why not just use synaptic to do it?

---

### Post by incubus on 2006-03-03
Yep, that command will do it. If you want to completely remove it including the configuration files, you could:
sudo apt-get remove --purge <package name>

And yeah, as Ressurection pointed out, you could also use Synaptic or Adept to remove it.

A program that you may consider installing is "deborphan". It tries to tell you the packages that don't seem to be used by others anymore.

incubus

PS: By the way, what was the problem with Fluxbox? It's a great windows manager. Also, have you tried XFCE4?

---

### Post by qwazert on 2006-03-03
Thanks...


FLuxbox crashed the moment I tried starting it. I'll give that XFCE4 thing a try.

---

