---
title: "show recent installed programs ?"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by medya on 2007-05-17
is there any way to see the recent installed programs ? (for example the last 10 installed programs in synaptic package manager or using apt-get install command ...)

---

### Post by derekguy on 2007-05-17
Using Synaptic you can get the history of what you have installed/removed/upgraded etc...

[highlight]File > History[/highlight]

I think this is what you are asking but I imagine there are some more powerful options using the command line but I can't find anything after a cursory look.

Hope this helps :popcorn:

---

### Post by tkjacobsen on 2007-05-17
apt-get and synaptic downloads packages to the same folder. You can use 
```
ls -lt /var/cache/apt/archives/ | more     
```
to see the packages sorted by date. You can use this if you installed packages with apt-get and not synaptic. (The quick and dirty way)

BTW:
It is not always packages in this folder are installed !!!

---

### Post by medya on 2007-05-17
by the way have you noticed how ugly and how slow the synpatic is ? isnt any way to make it smoother and faster? like using mysql for database ?

---

### Post by medya on 2007-05-17
I think thats what ubuntu should work on for the next release, we need a beautifull and fast thing instead of package manager...

there are many features which they can include, like installing multiple programs at once...or .

---

