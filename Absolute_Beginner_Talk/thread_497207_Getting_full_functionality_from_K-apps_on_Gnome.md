---
title: "Getting full functionality from K-apps on Gnome"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by abben on 2007-07-10
I use Gnome ubuntu, and have been using a few great "K" applications, like RSI break, Kdissert, and Akregator. I like Kdissert and Akregator more than any gnome alternatives I have found thus far, and I just plain don't even know of a gnome alternative to RSI break.

But, some functionality is missing from each of these, presumably because they are made for the K desktop.

Kdissert - A mindmapping program, has the awesome feature of linking to other real documents within mind map. But it can not launch them when I click on them, so that whole sphere of the program is off limits.

Akregator- News aggregator. I can open an article in a new tab, but I can not open in an external browser.

RSIbreak - I have configured it to auto-load on startup, but it still doesn't. Presumably because I'm on Gnome (is that "Gee-nome" or "nome"?).

Anyway... is there any fix for this? I suppose I could go over to Kubuntu, its just that I have regular ubuntu presently installed, it would be neat if there were a simple fix..

---

### Post by wolfen69 on 2007-07-10
it may be that certain dependancies arent being installed.

---

### Post by davidjmayo on 2007-07-10
> Anyway... is there any fix for this? I suppose I could go over to Kubuntu, its just that I have regular ubuntu presently installed, it would be neat if there were a simple fix..

Install the KDE desktop in a terminal

```
sudo aptitude update && sudo aptitude install kubuntu-desktop
```

guide here if you need it [http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

You can choose which session to use when you login. On Gnome on the left click where it says sessions.
From the kubuntu login screen right click on the icon by username and password to select the session type.

---

