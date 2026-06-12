---
title: "deb installer is broken"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by zp3dd4 on 2008-02-24
For some reason, whenever i use the deb installer to install any application, i get:

Installation finished

Failed to install package ________ .deb

and the terminal open with:

Selecting previously deselected package fityk.
(Reading database ... 

:(

thx

---

### Post by Crooksey on 2008-02-24
```

$ sudo dpkg -i /path/to/pkg/<pkgname>

```

And post exact output.

---

### Post by zp3dd4 on 2008-02-25
hmm... using command line, it installs, but it doesn't using the graphical interface :S

---

### Post by Crooksey on 2008-02-25
Not sure on that one then, I use the command line for everything as I find the GUI package management 1)  isnt for me and 2), doesent always work.

If the problem is the same with all .deb packages, then file a bug.

---

### Post by stoodleysnow on 2008-02-25
reinstall synaptic and gdebi?

---

### Post by zp3dd4 on 2008-02-25
hmm.. well its only the gui thats messed up. I tried reinstalling gdebi but it doesnt solve it :S

---

