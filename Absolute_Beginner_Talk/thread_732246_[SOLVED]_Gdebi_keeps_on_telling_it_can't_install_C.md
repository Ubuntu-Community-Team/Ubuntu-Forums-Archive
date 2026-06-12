---
title: "[SOLVED] Gdebi keeps on telling it can't install Cairo dock?"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by drazgo on 2008-03-22
hi everybody, 

I am trying to install the newest version of cairo dock on my ubuntu installation. But when i try to install it, gdebi keeps on telling the package might be corrupt or that i may not have the right perms to install it. But i downloaded the package several times + i do have perms to install...

any ideas?
Thanks!

---

### Post by drazgo on 2008-03-23
anyone? :confused:

---

### Post by linuxtoindia on 2008-03-23
please specify the exact error messege

---

### Post by drazgo on 2008-03-23
well, that's pretty much it :P it just says that i either don't have permission to use the package or that the package is corrupt...

---

### Post by drazgo on 2008-03-25
nevermind! found it! there is a problem with the download dir of belios. I just downloaded the package off the repos, and that installed just fine! for people with same problem, add this repo to synaptic: 

deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) gutsy cairo-dock

and install using synaptic ;)

---

