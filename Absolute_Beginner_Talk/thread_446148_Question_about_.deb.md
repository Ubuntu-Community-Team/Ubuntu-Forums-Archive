---
title: "Question about .deb"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by Yaffle on 2007-05-16
Hello,
I was wondering if .deb packages  update them self once installed? eg: if an new version come out?

---

### Post by rich.bradshaw on 2007-05-16
Only if there is a repository for them to be updated from.

I.e. if I manually download firefox as a deb and install it will, but if I install something not in the repos then no.

For 90% of things therefore the answers no, as why would you manually download something in a repo.

If you run

ls /var/cache/apt/archives/

You will see that everything you download with apt is actually a .deb.

---

### Post by Oki on 2007-05-16
No, and thats why you can find different versions of the same program on this site; [http://www.getdeb.net/](http://www.getdeb.net/) 

But if you install a deb file you can find it in synaptic(So if you install as an example pidgin as from a deb file you can later search it up in Synaptic to remove it). So if there gets out a new version of the program(and a new deb file), you can remove the first one before you install the next.

---

