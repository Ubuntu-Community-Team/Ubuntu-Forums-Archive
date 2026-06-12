---
title: "Problem with open office 2.2"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by jwinst on 2007-08-05
anyone got an idea why I have this upon installation?

First time opening it by the way, reinstalled it several times

[http://i14.photobucket.com/albums/a335/jwin05/screenshot2.png](http://i14.photobucket.com/albums/a335/jwin05/screenshot2.png)

---

### Post by wolfen69 on 2007-08-05
what's the problem? language?

---

### Post by jwinst on 2007-08-05
I haven't the slightest; like I said, it was my first time opening it up.  I can't change any settings because I can't read anything, and I've reinstalled it a few times and it wasn't any help.

---

### Post by asmoore82 on 2007-08-05
open a terminal and run 'locale' and make sure you are set to en_US.

if that's okay you might want to nuke all of openoffice's personal options and run it again.

```
~ $ locale
~ $ mkdir .backups
~ $ mv .openoffice* .backups/
```

---

### Post by jwinst on 2007-08-05
I tried this, didn't fix it :(

---

### Post by alienexplorers on 2007-08-05
If you open tools options in open office and change the default location to en-US does that help.  It looks like the default language is not set correctly.  You could always go into synaptic and delete open offfice and then reload it with the en-US options selected.

---

### Post by jwinst on 2007-08-05
seems to work now, I completely nuked it in package manger, apparently using the reinstall option doesn't work as well as completely removing then installing

---

