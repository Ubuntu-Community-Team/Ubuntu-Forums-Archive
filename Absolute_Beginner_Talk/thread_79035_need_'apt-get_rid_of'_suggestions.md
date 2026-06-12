---
title: "need 'apt-get rid of' suggestions"
date: 2005-10-19
forum: Absolute Beginner Talk
---

### Post by fuscia on 2005-10-19
i've already used the synaptic package manager to dump gaim, games and openoffice. i use my computer for e-mail (evolution), internet (firefox), pics (gimp) and listening to music. i don't have a DVD player. so, what else can i dump? some of this stuff is gibberish to me and i don't know if i need it or not. thanks.

---

### Post by aysiu on 2005-10-19
How are we supposed to know what programs you don't use? I'm confused by your question. Are you hurting for hard drive space? Is that why you want to dump all these programs? Ubuntu comes with only one program per task--it's not exactly bloat.

---

### Post by Ampersand on 2005-10-19
Have a look through the world wide web and and multimedia sections to start with. If you mark a package to be removed you'll be told if something else will be removed at the same time.

If you want to free up some disk space, try running
```
sudo apt-get clean
```
This will delete the .deb files for the packages you've installed.

---

