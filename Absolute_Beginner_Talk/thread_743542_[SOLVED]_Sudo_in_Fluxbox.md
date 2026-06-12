---
title: "[SOLVED] Sudo in Fluxbox"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by AnLGP on 2008-04-02
There's a post for this already, but I looked and it's not answered.

I'm aware I can type sudo synaptic and install as root but what I want is to be able to right click and bring up the menu, click on synaptic and have it prompt me for a password.

Is this possible?

If not I can just do it via the CL, but this sure would be faster.

---

### Post by spupy on 2008-04-02
```
gksu synaptic
```
Use this command - it will popup the box that ask for sudo pass, the one that dims the rest of the screen.

---

### Post by AnLGP on 2008-04-02
Thanks a bunch!

---

