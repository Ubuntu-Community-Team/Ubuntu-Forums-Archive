---
title: "Adding applications to Applications"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by Ansible on 2008-04-03
I've written a couple of applications for ubuntu.  One is a game using SDL.  The other is a time tracker using GTK.  I created application launchers for them in the 'Applications' menu, but from there I can only launch the game, not the GTK app.  I can still launch the GTK app by going to it in Nautilus and double clicking.  Any ideas?

---

### Post by InfinityCircuit on 2008-04-03
What happens if you run the GTK application in a term? Does it give you any error messages?

---

### Post by Ansible on 2008-04-03
Yeah a few:

```
(TimeKeeper:9411): libglade-WARNING **: could not find signal handler 'on_cut1_activate'.

(TimeKeeper:9411): libglade-WARNING **: could not find signal handler 'on_paste1_activate'.

(TimeKeeper:9411): libglade-WARNING **: could not find signal handler 'on_copy1_activate'.


```

But they seem relatively harmless... glade couldn't find a couple functions I haven't implemented yet.  I guess I can take those out...

---

### Post by Ansible on 2008-04-03
Removed those ftn references from the glade XML file, no errors from command line.  Still no dice on the launch though.

---

