---
title: "litconverter help"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by jonathan21 on 2007-04-17
what should i do i get the following error trying to open litconverter

Traceback (most recent call last):
  File "/usr/share/litconverter/main.py", line 13, in ?
    from PyQt4 import QtCore, QtGui
ImportError: No module named PyQt4

---

### Post by Andy_D on 2007-04-17
You could try installing the python-qt4 package using synaptic, or from the command line by typing:

```
sudo apt-get install python-qt4
```

I hope that helps.

---

