---
title: "Automatix2 Problem"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by SnakeByte29 on 2007-06-13
Lately, every time I (try to) use Automatix2, I get an error message saying,"An apt-based error occurred and installation was unsuccessful." I can install the same program through apt-get or Synaptic, but Automatix2 is just easier and I'd like to know what the problem is. Can anyone shed some light on this?

---

### Post by alienexplorers on 2007-06-13
You should ask the question in the Automatix2 forum, not here.

---

### Post by violin on 2007-06-13
try to reinstall it

sudo apt-remove automatix


hope this helps

---

### Post by STREETURCHINE on 2007-06-13
it is best to ask for help on the automatix forum there is a link in my signature below

---

### Post by arnieboy on 2007-06-14
> **SnakeByte29 said:**
> Lately, every time I (try to) use Automatix2, I get an error message saying,"An apt-based error occurred and installation was unsuccessful." I can install the same program through apt-get or Synaptic, but Automatix2 is just easier and I'd like to know what the problem is. Can anyone shed some light on this?

Please paste the results of the following 3 commands:
```
cat /etc/apt/sources.list
```
```
sudo apt-get update
```
```
sudo apt-get -f install
```

---

