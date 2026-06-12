---
title: "How to install multiple packages"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by rajeshgovindan on 2006-11-14
How to install multiple packages from the terminal ?
i.e interdependent packages

Thanx in advance

Rajesh

---

### Post by dillbertdabomb on 2006-11-14
if you download the files, like me, you just click them for the graphical way, but for the term. way you type in sudo dpkg -k pack.deb or somtin like that, it's in the help section

---

### Post by Bachstelze on 2006-11-14
It's dpkg -i, like **i**nstall. Do

```
sudo dpkg -i package1.deb package2.deb ... packageN.deb
```

You can also use *.deb, will install all the DEBs in the current dir.

---

