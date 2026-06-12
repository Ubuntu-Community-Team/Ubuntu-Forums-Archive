---
title: "[SOLVED] PLF ubuntu repositories with kubuntu?"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by leetrefz on 2006-11-19
Will the ubuntu PLF repositories work with kubuntu?

---

### Post by Perfect Storm on 2006-11-19
Yes. (why shouldn't it?)

---

### Post by leetrefz on 2006-11-19
Well I don't know, I thought maybe there would be some gnome/kde discrepancy. I know it'll basically work, but I just don't know if whatever I download will appear like gravy in the k menu as with stuuf from the offical repositories.

---

### Post by Perfect Storm on 2006-11-19
Usually when it doesn't appear in the menu, just type the name of it in the terminal/konsole.

---

### Post by leetrefz on 2006-11-19
What do I do about this that came up in synaptic when I tried to put those repositories in?
> W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) edgy-plf Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718


---

### Post by rocktorrentz on 2006-11-21
> **leetrefz said:**
> What do I do about this that came up in synaptic when I tried to put those repositories in?

Try this:
```
wget http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg -O- | sudo apt-key add -
```

---

