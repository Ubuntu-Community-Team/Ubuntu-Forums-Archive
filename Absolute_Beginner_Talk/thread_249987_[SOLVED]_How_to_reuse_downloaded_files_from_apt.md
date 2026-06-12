---
title: "[SOLVED] How to reuse downloaded files from apt?"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by argie on 2006-09-03
Are the files downloaded using apt-get stored anywhere where I can copy it to a CD so that I can update a system which doesn't have the internet access?

If there's some kind of a limit to how many such files are stored, is it possible to change it?

---

### Post by taurus on 2006-09-03
They are all in /var/cache/apt/archives...

---

### Post by argie on 2006-09-03
All? Oh wow, thanks.

---

### Post by whizbaby on 2006-09-03
They are stored in /var/cache/apt/archives until you do apt-cache clean.

To locate stuff on your system use (from terminal) **locate**. To get it started type **sudo updatedb** (which you will have to do from time to time and usually only takes a little the first time). As an example to locate any packages, type:

**locate *.deb**

for mp3's

**locate *.mp3**

and so on...

---

### Post by taurus on 2006-09-03
> **argie said:**
> All? Oh wow, thanks.
Yes, all of them including a kitchen sink...

---

### Post by argie on 2006-09-03
Heck, that was fast. Thanks for the help and the tips.

---

