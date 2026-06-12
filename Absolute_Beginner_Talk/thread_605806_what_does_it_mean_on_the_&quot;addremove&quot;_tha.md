---
title: "what does it mean on the &quot;add/remove&quot; that an application is not authenticated?"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by someoneouthere on 2007-11-07
is not yet aproved? at my own risk?

---

### Post by oldos2er on 2007-11-07
Probably means you're missing a repository's gpg key.

---

### Post by Paul820 on 2007-11-07
That usually means you are using a repository that ubuntu has no control over. It hasn't been checked by ubuntu and it could damage your system,  Did you edit your etc/apt/sources.list and add anything to it?

---

### Post by someoneouthere on 2007-11-07
not really... which repositories are safe? and how to..

---

### Post by Paul820 on 2007-11-07
What does your sources.list look like? If there are only cononical.com and ubuntu.com then you will be fine, oh and medibuntu.org as well. Any others you add to that list you do so at your own risk. If you know that the repo is safe, then you have nothing to worry about. If you do only have canonical and ubuntu repos in there, then just ignore the warnings.

---

### Post by someoneouthere on 2007-11-07
can i find a directory which lists or something like that the "safe-popular" repositories?

---

### Post by maybeway36 on 2007-11-07
tell it to update, or run
```
sudo apt-get update
```
see if that fixes it.

---

