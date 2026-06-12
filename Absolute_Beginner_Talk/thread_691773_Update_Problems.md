---
title: "Update Problems"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by HappyEisentrout on 2008-02-09
I have some updates for Firefox, particularly a flash update.  But when I try to update it doesn't let me, and then I get the updates available icon on my upper bar and when I try to update I get this message.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Anyone know what that means or how to fix it?

---

### Post by spiderbatdad on 2008-02-09
in a terminal run ```
sudo dpkg --configure -a
```

---

### Post by taurus on 2008-02-09
Close the Update window.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by HappyEisentrout on 2008-02-09
I did all that and at the end it says this...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 python-sqlalchemy
 griffith
E: Sub-process /usr/bin/dpkg returned an error code (1)

Ummm, is that bad?

---

### Post by spiderbatdad on 2008-02-09
that python package is not installed by default. did you install it yourself? it may have unmet dependencies: like griffith, which is in synaptic.

---

