---
title: "sources.list source-o-matic"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by amrclutch1 on 2007-08-09
Will the source-o-matic for ubuntu work on debian?

---

### Post by rich.bradshaw on 2007-08-09
Possibly, but wouldn't recommend using it on Ubuntu, let alone something it's not supported on!

Why do you want it?

---

### Post by amrclutch1 on 2007-08-09
Well I want to install xorg on debian and it says xserver-xorg and xorg are not found. I did a sudo apt-get update and only 1 byte of data is found. I need a good debian source list!
[B]
EDIT:[/B] Oh, and I have a minimal install, only a command line.

---

### Post by Seisen on 2007-08-09
Which version of Debian are you using?

---

### Post by aysiu on 2007-08-09
I wouldn't use Ubuntu repositories for a Debian installation.

[This site](http://www1.apt-get.org/search.php?query=xorg&submit=Submit+Query&arch%5B%5D=i386&arch%5B%5D=all) may help you, though.

---

### Post by amrclutch1 on 2007-08-09
Whatever the newest version of debian is now is what I am using.

---

### Post by aysiu on 2007-08-09
> **amrclutch1 said:**
> Whatever the newest version of debian is now is what I am using.
It doesn't matter what version of Debian you're using--don't use Ubuntu repositories with Debian. You'll break your system.

---

### Post by amrclutch1 on 2007-08-09
Ok, the site you gave me is slow loading :P but I see that it has a list, but I don't know what to choose :o

---

### Post by aysiu on 2007-08-09
> **amrclutch1 said:**
> Ok, the site you gave me is slow loading :P but I see that it has a list, but I don't know what to choose :o
I don't know either, which is why I gave you the list instead of a particular repository set.

They should all be Debian-compatible, though.

---

