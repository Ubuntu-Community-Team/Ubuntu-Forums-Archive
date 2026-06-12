---
title: "[SOLVED] error with ./configure No package 'glib-2.0' found (2)"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by Jelmoh on 2008-01-03
I've found a thread on this forum that describes my problem exactly, but it's not solved..
[Here](error with ./configure No package 'glib-2.0' found) is the thread I mentioned, at the bottom you see my post with a description of my problem.
I hope you can help, I tried a lot but nothing works for me...

---

### Post by Borbus on 2008-01-03
Did you install build-essential package?

---

### Post by Jelmoh on 2008-01-03
I didn't, but even now I did, it doesn't solve the problem..
Still the same "glib-2.0 not found"

---

### Post by K.Mandla on 2008-01-03
Usually when you see "not found" messages like that, you need to install the development files for the software it wants.

[http://packages.ubuntu.com/gutsy/libdevel/libglib2.0-dev](http://packages.ubuntu.com/gutsy/libdevel/libglib2.0-dev)

libglib2.0-dev is probably what you need.

---

### Post by adam.tropics on 2008-01-03
As I think was previously mentioned, anjuta is actually in the repos, without needing to compile. Try installing 'libglib2.0-dev' if you still need to compile.

edit: too slow again, lol!

---

### Post by Jelmoh on 2008-01-03
Thanx, that solved the glib problem...
now I have GTK2.0... same issue.. same error...
glib-2.0 changed into gtk+-2.0..
Thanx for all your help! could you help me with this too?

---

### Post by adam.tropics on 2008-01-03
Well you could (you'll need source repos enabled....just a checkbox in synaptic prefs)
```
sudo apt-get build-dep anjuta
```...but honestly, I am a tad confused, anjuta is in the repos anyway, and if you need a newer version, there are more repos, and a guide posted at [the anjuta site]("http://anjuta.sourceforge.net/downloads"). They have newer versions.

---

### Post by K.Mandla on 2008-01-03
> **Jelmoh said:**
> Thanx, that solved the glib problem...
now I have GTK2.0... same issue.. same error...
glib-2.0 changed into gtk+-2.0..
Thanx for all your help! could you help me with this too?
How about ...

[http://packages.ubuntu.com/gutsy/libdevel/libgtk2.0-dev](http://packages.ubuntu.com/gutsy/libdevel/libgtk2.0-dev)

It can be a little tricky to figure out which package it wants or needs. Things like GTK or glib are sometimes prefaced with lib*, and suffixed with their version, and the -dev tag.

If you run into another one, try searching for it on the package search page, just to learn how it works. 

[http://packages.ubuntu.com](http://packages.ubuntu.com)

If you still can't find it, ask us and we can help.

---

### Post by Jelmoh on 2008-01-03
I didn't want ajunta.. else I installed via other ways...
But thanks for the help! really! :D
I'll figure the rest out myself, thanks for the website K.Mandla! :)

---

### Post by adam.tropics on 2008-01-03
Oops! Tried to find the thread with the same problem you mentioned, via your post search....forgot to actually read your post there!!

...but having read your post

```
 sudo apt-get install sensors-applet
```

---

### Post by Jelmoh on 2008-01-03
just that simple.. sigh.. sorry guys.. :P
but thanks for your help! I'll look for the simple solutions next time...:P

---

