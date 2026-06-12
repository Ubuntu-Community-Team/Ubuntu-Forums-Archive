---
title: "delete programs"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by noob_1 on 2007-09-14
i want to be able to completely delete a program i downloaded from the internet. i didn't download through synaptic, but straight from site direct download, and can't seem to through add/remove. help.

---

### Post by Tyke91 on 2007-09-14
was it a .deb or tarball?

---

### Post by noob_1 on 2007-09-14
it was .deb

---

### Post by mikewhatever on 2007-09-14
Try > sudo dpkg -P name-of-the-frogram

---

### Post by SOULRiDER on 2007-09-14
or
```
sudo aptitude purge <name>
``` so it removes all the config files too.

---

