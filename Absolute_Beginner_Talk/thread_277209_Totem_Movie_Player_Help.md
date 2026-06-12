---
title: "Totem Movie Player Help"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by spyker3292 on 2006-10-14
When I try to play a .mov file it says I need a plugin. Where can I find this and how do I install it? Is there a player that can play .mov w/out a plugin?

---

### Post by timetunnel on 2006-10-14
You'll need (at least) the following package:

w32codecs

It's not in the ubuntu repository, but you can get it by adding the repository from [PLF]("http://doc.ubuntu-fr.org/doc/plf") to your package sources (look there for instructions).

I'm not sure if that package is sufficient. Maybe you'll need some more gstreamer packages as well. I just installed the following packages as well and now can play almost everything:

gestreamer0.10-plugins-good
gestreamer0.10-plugins-bad
gestreamer0.10-plugins-bad-multiverse
gestreamer0.10-plugins-ugly
gestreamer0.10-plugins-ugly-multiverse

---

### Post by deadgobby on 2006-10-14
you can all so look for quick time plug in too in Synaptic. Just time in quick time and shall find and install. 

Gobby

---

