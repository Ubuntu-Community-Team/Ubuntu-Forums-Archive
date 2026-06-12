---
title: "gnome-btdownload"
date: 2006-05-21
forum: Absolute Beginner Talk
---

### Post by Nikusan on 2006-05-21
How do I set the port that gnome-btdownload listens on? I've poked around in gconf-editor but can't find anything.

---

### Post by it.henrik on 2006-05-21
the default ports according to the bt protocol (if you can say there is one) are 6881-6999. starting at 6881 and then increase +1 for every new torrent you are dl:ing ... if you want more control of whats going on I recommend Azureus.

---

### Post by Nikusan on 2006-05-21
[QUOTE=it.henrik]the default ports according to the bt protocol (if you can say there is one) are 6881-6999. starting at 6881 and then increase +1 for every new torrent you are dl:ing ... if you want more control of whats going on I recommend Azureus.[/QUOTE]

Are you saying that btdownload listens on the first port it can bind to in that range and it's impossible to change it to anything else? ](*,)  I'm usually the first to stand up and defend Gnome's "sane defaults" UI policy against my KDE zealot friends but this really isn't a sane default... Many ISP's interfere with BT data, making changing the port out of that range necessary. 

I'm trying to avoid using azureus because it's a pig and doesn't perform well on the low spec machine I want to run it on. Even the GCJ version in the repos is bad and has a whole bunch of its own bugs.

I guess I'll use a client that falls somewhere in between the two. Thanks for the reply :)

---

### Post by it.henrik on 2006-05-21
bittornado is something between

---

### Post by GarethMB on 2006-05-21
Or you can try uTorrent under wine.

---

### Post by Jussi Kukkonen on 2006-05-21
[QUOTE=GarethMB]Or you can try uTorrent under wine.[/QUOTE]
Isn't that a _little_ overkill? There are ten different native BT clients in the repositories.

Nikusan: you've got two choices:
* Start gnome-btdownload with options *--minport* and *--maxport* (I've heard the next version will have these in gconf).
* Use bittorrent-gui (it's minimal, but not as much as gnome-btdownload)

---

### Post by Nikusan on 2006-05-21
[QUOTE=Jussi Kukkonen]
* Start gnome-btdownload with options *--minport* and *--maxport* (I've heard the next version will have these in gconf).
[/QUOTE]

That's exactly what I wanted, ta :)

---

### Post by Rizado on 2006-06-14
[QUOTE=Nikusan]That's exactly what I wanted, ta :)[/QUOTE]You know that if you put "man" infront of a command you'll see the manual. eg "man gnome-btdownload". There all options are listed.

---

