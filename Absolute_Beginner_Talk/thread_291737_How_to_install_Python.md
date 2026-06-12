---
title: "How to install Python?"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by DMPineau on 2006-11-02
Okay, so I'm running Kubuntu 6.10 and trying to install Cedega. When I try to depackage using the command 'sudo dpkg -i /home/dmpineau/Desktop/cedega-small_5.2.3_all.deb' I get this message in terminal:

Selecting previously deselected package cedega-small.
(Reading database ... 77938 files and directories currently installed.)
Unpacking cedega-small (from .../cedega-small_5.2.3_all.deb) ...
dpkg: dependency problems prevent configuration of cedega-small:
 cedega-small depends on python-gtk2 (>= 2.6); however:
  Package python-gtk2 is not installed.
 cedega-small depends on python-glade2; however:
  Package python-glade2 is not installed.
dpkg: error processing cedega-small (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 cedega-small

So obviously I need to install Python. Kubuntu should come with some version of python-kde right? Well I can't figure out how to install what I need.. somebody should shoot me some command lines ;)

---

### Post by user1397 on 2006-11-02
maybe cedega only works with gtk, and not qt (kde), so try:
```
sudo apt-get update&&sudo apt-get install python-gtk2 python-glade2
```

---

### Post by %hMa@?b&lt;C on 2006-11-02
sudo aptitude install python-gtk2 python-glade2

---

### Post by DMPineau on 2006-11-02
> **jeffc313 said:**
> sudo aptitude install python-gtk2 python-glade2

Aha. That did it. Thanks guys!

---

