---
title: "Repositories... can't remember"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by julie_lebou on 2007-03-22
I don't remember how to go in the repositories... well I tough I did, but when I open the synaptic package manager, then settings, then repositories... the tabs do not refer to repositories. I know I accessed them before... but how?

---

### Post by konst88 on 2007-03-22
sudo gedit /etc/apt/sources.list

---

### Post by buuntuu! on 2007-03-22
> **julie_lebou said:**
> I don't remember how to go in the repositories... well I tough I did, but when I open the synaptic package manager, then settings, then repositories... the tabs do not refer to repositories. I know I accessed them before... but how?

this is your chance to get to know the allmighty command line ;)
```
sudo gedit /apt/sources.list
```
just uncomment (remove the # at the beginning of the line of) all the repositories you want to use, save, exit, done :)

---

### Post by julie_lebou on 2007-03-22
How wierd... i did that before, there was stuff there.. but i did it this time... theres nothing showing up there! 

Nope, nothing, the page is blank

---

### Post by julie_lebou on 2007-03-22
Found it... the first post had the correct code, but not the second

---

### Post by meborc on 2007-03-22
you probably entered a wrong path... this created a new empty file... be sure the path is ```
sudo gedit **/etc/apt/sources.list**
```not```
sudo gedit **/apt/sources.list**
```:D

EDIT: ahh... you were quicker

---

### Post by julie_lebou on 2007-03-22
But... I tough there was a way to view what pro grammes were in each repository? I'm lost here

---

### Post by buuntuu! on 2007-03-22
sorry for that typo there!
to see what repositories certain apps are in, just open synaptic as you did before and select "sections" the repos are mentioned there...

---

