---
title: "Installing programs"
date: 2006-06-03
forum: Absolute Beginner Talk
---

### Post by IrishGangsta on 2006-06-03
i need to install macromdedia flash player manually and i have no idea how to do that.
Also, what should i use to download music with linux?
i typed this one thing in the terminal and it said i was locke dout and asked if i was administrator

Any help is much aprreciated!](*,)

---

### Post by bman on 2006-06-03
to be administrator in the terminal, type su, then enter your password

---

### Post by CompShrink on 2006-06-03
Just go to System > Administration > Synaptic, and search for "flash" install the nonfree version listed. Then firefox will play flash. Firefox cannot install it automatically like on windows, but you can still let synaptic install it automatically.

In Synaptic you can search for **peer to peer** in Synaptic, just change the drop down box that says* name* to *description and name* and look through the results.

---

### Post by aysiu on 2006-06-03
I don't see why you need to install it manually.

Just [make sure you have extra repositories enabled](http://www.psychocats.net/ubuntu/sources) and then ```
sudo aptitude update
sudo aptitude install flashplugin-nonfree
```

---

