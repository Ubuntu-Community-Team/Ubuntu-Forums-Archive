---
title: "updates"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by nicholas mccarthy on 2007-11-04
i exited the update thing before it was done updating, and now it wont work. what do i do?

---

### Post by SOULRiDER on 2007-11-04
Was it downloading or installing? And what kind of errors do you get?
Try doing (in a terminal)
```
sudo aptitude update
sudo aptitude dist-upgrade 
```

Paste any errors you may get.

---

### Post by nicholas mccarthy on 2007-11-04
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

it was installing them, but it froze, so i force quitted it.

---

### Post by SOULRiDER on 2007-11-04
Do this:
```
sudo dpkg --configure -a
```

After that I suggest you do
```
sudo aptitude update
sudo aptitude dist-upgrade
```

---

### Post by nicholas mccarthy on 2007-11-04
thanks. it worked

ya, im still on 6.10, and its 12:30 at night (i thought id be able to at least get the installation started by 12 for 7.04, lol)

---

