---
title: "fuse update problem"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by Drakkor on 2007-01-30
See screenshiot.  Anyone ?

---

### Post by taurus on 2007-01-30
Just answered the same thread from another user.

Applications -> Accessories -> Terminal
```
sudo aptitude clean
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by sonny on 2007-01-30
In a terminal Applications>Accesories>Terminal write the following:

```
sudo apt-get update
```Once it has finished re-loading the repositories, do:
```
 sudo apt-get dist-upgrade
```

---

### Post by Drakkor on 2007-01-30
Thanks, taurus , it worked like a charm !  :D

---

