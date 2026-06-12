---
title: "Help"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by horsehead on 2008-01-18
When trying to install using Add/Remove programs, Synaptic Package Manager, Software updates, keep getting the following error:
E:dpkg was interupted you must manually run 'dpkg--configure-a' to correct problem
E:_cache->open()failed,please report

How do I do this, I am totally lost on this.

---

### Post by Cypher on 2008-01-18
Open up a terminal with Applications->Accessories->Terminal and type
```

sudo dpkg-configure -a

```
Oh and next time please make a more descriptive post title than "Help"..

---

### Post by horsehead on 2008-01-18
sudo dpkg-configure -a
I get a reply of command not found

---

### Post by lswest on 2008-01-18
it's ```
sudo dpkg--configure -d
``` (two hyphens after the dpkg)

---

### Post by oldos2er on 2008-01-18
It's "sudo dpgk --configure -a"
There's a space between dpkg and --configure

---

