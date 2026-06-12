---
title: "Ubuntu repository downloads"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by calvinthomas on 2006-07-26
Ok, I didn't know how to write a subject line for this but basically what I want to know is where ubuntu saves the files it downloads for installing packages when I have used synaptic package manager or add/remove, i'm a little tight on space and could do with freeing up the undoubted large amount that is in there (i've been fiddling so i've downloaded lots)

Calv

---

### Post by qamelian on 2006-07-26
> **calvinthomas said:**
> Ok, I didn't know how to write a subject line for this but basically what I want to know is where ubuntu saves the files it downloads for installing packages when I have used synaptic package manager or add/remove, i'm a little tight on space and could do with freeing up the undoubted large amount that is in there (i've been fiddling so i've downloaded lots)

Calv

Just type:
```
sudo aptitude clean
``` in a terminal and this will clean out all the .debs in your package cache.

---

### Post by calvinthomas on 2006-07-27
Perfect, thankyou an extra gig and a bit!

Calv

---

### Post by kinematic on 2006-07-27
the packages that synaptic downloads are kept in /var/cache/apt/archives.
you can set synaptic to remove them after installing packages.
properties>preferences>packages and check the box "remove packages after installation".

---

