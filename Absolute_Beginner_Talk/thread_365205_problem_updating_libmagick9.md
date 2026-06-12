---
title: "problem updating libmagick9"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by kaplis on 2007-02-19
hey

while updating, such a message appeard-

E: /var/cache/apt/archives/libmagick9_7%3a6.2.4.5.dfsg1-0.10ubuntu0.2_i386.deb: corrupted filesystem tarfile - corrupted package archive

update manager shows Download size: none to this file

any ideas?

---

### Post by ashmew2 on 2007-02-19
y dont u try removing it completely and diong a fresh install ?

In terminal :

```
sudo rm /var/cache/apt/archives/libmagick9_7%3a6.2.4.5.dfsg1-0.10ubuntu0.2_i386.deb
```

Then
```
sudo apt-get upgrade
```

For a total system update~!!

---

### Post by kaplis on 2007-02-19
thank you=paldies

---

### Post by ashmew2 on 2007-02-20
what means paldies ? :P

---

