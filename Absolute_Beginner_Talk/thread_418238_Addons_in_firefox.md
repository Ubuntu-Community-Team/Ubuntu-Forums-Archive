---
title: "Addons in firefox"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by tribunal on 2007-04-22
After installing Kubuntu Feisty, I can't install addons in Firefox Sad
everything I see is "error 203"
I have found (during googling), that I should start firefox with sudo (as root)
But I can't Sad
sudo firefox just doesn't work:
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(firefox-bin:15263): Gtk-WARNING **: cannot open display:

Any ideas?
(2 problems: addons and starting firefox as root)

---

### Post by amaroKer on 2007-04-22
I'm sure that you don't need to start Firefox as root.  Not entirely sure about the other thing.  Is this a fresh install?  Have you messed with Firefox config at all?  Maybe try _[Swiftfox]("http://www.getswiftfox.com/")_.

---

### Post by tribunal on 2007-04-22
Thank you!
I have found solution! :)
The problem was here: it wasn't fresh installation, kubuntu was installed right after suse
so, /home directory was old
So, solution is here: clean ~/.mozilla dir (one file in this directory: extenstions.rdf)

---

