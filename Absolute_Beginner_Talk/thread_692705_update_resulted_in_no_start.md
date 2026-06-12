---
title: "update resulted in no start"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by whits on 2008-02-10
the latest ubuntu update(I think it was to kernel) resulted in no startup in 2.6.22-14-386 I can only use old one 2.6.20-16 and that has low res only I am not up with command use so if there is a fix please keep it in simple terms

---

### Post by kaiju on 2008-02-16
you could try running the upgrade process again, from a terminal window (e.g. gnome-terminal)
```
sudo apt-get upgrade
```
(note that you will be prompted for your login password, but no stars or dots will be displayed while you're typing it in)

in case the startup problem resulted from a broken upgrade, apt-get will usually suggest you how to fix it.

---

