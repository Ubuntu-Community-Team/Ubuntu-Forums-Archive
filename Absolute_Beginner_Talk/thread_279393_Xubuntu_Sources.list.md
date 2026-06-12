---
title: "Xubuntu Sources.list"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by PricklySponge on 2006-10-17
How do I get to sources.list in xubuntu?

---

### Post by enopepsoo on 2006-10-17
at the terminal, please type
```
sudo nano /etc/apt/sources.list
```

---

### Post by meng on 2006-10-17
Same way as in the other flavors. Drop to command line,
cat /etc/apt/sources.list
(that will just display the contents in the terminal)

---

### Post by PricklySponge on 2006-10-17
ok, thanks. I'm trying to install automatix into xubuntu and the instructions arent clear to me. Can somone explain how to do it? For instance, how do I uncomment something?

---

### Post by PricklySponge on 2006-10-17
Bump; what does it mean to uncheck something in sources.list in xubuntu?

---

### Post by ReaderRat on 2006-10-17
Anything in the list that has a # in front of it is considered to be a comment, and not code. To uncomment, you would remove/delete the #'s.
EDIT:   See the Automatix site below in my signature. The site is very bad on the eyes (red on black), but the instructions are there.

---

