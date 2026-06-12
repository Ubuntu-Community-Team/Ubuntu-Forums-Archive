---
title: "Question about importing Windows Firefox settings into Ubuntu 7.04 Firefox [Resolved]"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by darrellfjohnson on 2007-04-29
In Windows I have an extension for Firefox called Bookmark Backups which backups not only my bookmarks, but also my saved passwords, cookies, and all of that.  But I don't know where Firefox is installed in Ubuntu, or even if they are compatible.  I tried pasting the files into the Firefox profile folder in my Home folder, but that didn't work.

The files that I need to transfer are:

```
searchplugins (this is a folder)
bookmarks.html
cert8.db
cookies.txt
formhistory.dat
history.dat
hostperm.1
key3.db
localstore.rdf
persdict.dat
secmod.db
sessionstore.js
signons.txt
```

---

### Post by darrellfjohnson on 2007-04-29
bump

---

### Post by nanotube on 2007-04-29
all those files should go into the following directory:
```
~/.mozilla/firefox/XXXXX.default/
```
where XXX would be some random string of numbers/letters, and ~ stands for your home directory.

---

### Post by aysiu on 2007-04-29
C:\Documents and Settings\darrell\Application Data\Mozilla

is the same as

/home/darrell/.mozilla

.mozilla is a hidden folder, so you may have to press Control-H to see it.

---

### Post by darrellfjohnson on 2007-04-29
Thanks both of you.  That worked, although I had to change permissions to get it to work perfectly.  This install is almost usuable full time now, and more usuable than any other distro I've tried.

---

