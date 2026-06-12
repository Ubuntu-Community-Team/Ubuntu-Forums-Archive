---
title: "apt get or synaptic"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by dsyn on 2006-09-19
Hi, I've recently completely switched to ubuntu and I'm quite happy with the liberation linux presents.  So, before I go off and break ubuntu :D by installing tons of software, what is a safer way to install software apt get or through synaptic?

Thanks and I'm glad to be a part of the community.

---

### Post by Brownedwg89 on 2006-09-19
whichever you feel more comfortable with
synaptic is basically apt with a GUI

---

### Post by comppsyco on 2006-09-19
The best way is through the command aptitude, which works like apt-get, but for one thing.
When you install something, apt-get, synaptic, and aptitude all grab that thing and all the other packages that it relies on. But when you un-install, only packages that have been installed with aptitude and then removed with aptitude will have all those "orphaned" packages without a use removed as well.

---

### Post by dsyn on 2006-09-19
oh I see. I appreciate the help.

---

### Post by jISh on 2006-09-19
Apt-get is the most common and effective way to do it. You can use aptitude as well, but I tend to only use it for things that would have a lot of dependencies. For regular updates all you have to do is write this in your terminal
```
sudo apt-get update && sudo apt-get upgrade
```
then get a coffee or something.

---

### Post by dsyn on 2006-09-19
> **jISh said:**
> then get a coffee or something.

I love the refrences to coffee all over the place in these forums, espeacially to beans. funny and sooo true.

---

