---
title: "[SOLVED] last update"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by natman on 2008-02-08
I had an update messsage yesterday, something to do with flash in firefox, or something. But ever since i agreed to take the update firefox has been terrible, when i go anywhere near a flash site the whole thing grounds to a halt, i have to se konquer now, anyone know exactly what the update was or how to fix this?

---

### Post by jan quark on 2008-02-08
try this
```

sudo apt-get remove --purge flashplugin-nonfree -y && sudo apt-get install flashplugin-nonfree -y
```

---

### Post by natman on 2008-02-08
Thank you, that did seem to help, also the integrated chat thing yahoo was really giving trouble so canceled it, thanks for the help

---

### Post by jan quark on 2008-02-08
good to hear pls mark this thead as solved
see signature

thank you

---

### Post by Quilzas on 2008-02-08
I had the same problem.

But I found I had to uninstall the gnash Mozilla plugin before the flashplugin-nonfree plugin would work, even after reinstalling flashplugin-nonfree

---

