---
title: "Krusader won't start as root [Resolved]"
date: 2006-11-23
forum: Absolute Beginner Talk
---

### Post by chaka53 on 2006-11-23
Hi

Please excuse an absolute beginner but some help would be helpful

Whenever I am in Krusader and want to start it in root mode I get the following:

Can't start root mode krusader, because krusader or kdesu is missing from the path. Please configure the dependencies in Konfigurator!

I am loving Ubuntu:)

---

### Post by ewl1217 on 2006-11-23
Try pressing Alt+F2 and running
```
kdesu krusader
```

If that doesn't work try it with
```
gksudo krusader
```

---

### Post by chaka53 on 2006-11-23
gksudo worked - do I have to do this every time or can I set up krusader somehow.

Many many many thanks

Chaka53

---

### Post by aysiu on 2006-11-24
> **chaka53 said:**
> gksudo worked - do I have to do this every time or can I set up krusader somehow.

Many many many thanks

Chaka53
You can make a keyboard shortcut or launcher icon with the command ```
gksudo krusader
```

---

### Post by chaka53 on 2006-11-24
works like a charm

Many thanks

---

### Post by chaka53 on 2006-11-24
just a final chapter in the saga
I ran

 sudo apt-get install --reinstall kdebase-bin

which i got from somewhere on the forum and it fixed all applications looking for kdesu - including adept manager

---

### Post by bratliff on 2007-03-28
Super deal. Worked for me. NOw I can use Krusadaer as Root.
Thanks

ratliff

---

