---
title: "[SOLVED] Truecrypt and Forcefield"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by sagesparrow on 2007-11-24
I think I have installed both of these.  Truecrypt responds to terminal commands.  But I'm at a loss regarding Forcefield.  There is a file "forcefield_current_all.deb.1 /home/me but beyond that i don't know how to proceed.  Forcefield does not show up in Applications/Accessories or anywhere else that I can find to start it.  Any help?

---

### Post by Taboo Mirage on 2007-11-24
Type this:

```
sudo dpkg -i forcefield_current_all.deb.1
```

It should then install the Forcefield GUI for TypeCrypt and you should be able to access it from within the Applications > Accessories menu, I believe.

---

### Post by sagesparrow on 2007-11-24
that did it.  much thanks.

---

