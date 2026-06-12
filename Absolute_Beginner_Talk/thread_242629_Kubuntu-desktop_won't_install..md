---
title: "Kubuntu-desktop won't install."
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by ubunick on 2006-08-23
It says it won't install because language-selector-qt can't be installed because I'm missing something.  Here is the exact message:

"kubuntu-desktop:
 Depends: language-selector-qt but it is not going to be installed"

It won't install because I have "unresolvable dependencies" and it doesn't tell me which ones.  Any ideas? Thx.  Oh, and I'm now using the 386 kernel.

---

### Post by aysiu on 2006-08-23
Get a fresh sources.list:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Make sure you're replacing and not adding to your current list.

Then try again: ```
sudo aptitude update
sudo aptitude install kubuntu-desktop
```

---

### Post by ubunick on 2006-08-24
Alright, I'll give it a go when I'm home (at school right now).  Much thanks.

---

