---
title: "[SOLVED] Archive directory /var/cache/apt/archives/partial is missing."
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by sports fan Matt on 2008-01-18
ok, how badly did i hose my system and do i need to reinstall everything, i may have gone and deleted too many files in my usr folder with the cache...ugh

---

### Post by spiderbatdad on 2008-01-18
it was probably empty...just create it. not a good idea to go deleting files from usr. if you want to clear your cache, just open a nautilis window like your home folder and select Go>>clear history.

---

### Post by sports fan Matt on 2008-01-19
How do i create it?  I am assuming this is why i cant reload things (and not finding repositories also)

---

### Post by asmoore82 on 2008-01-19
```
sudo mkdir -p /var/cache/apt/archives/partial
```
in a terminal ("Applications -> Accessories -> Terminal")

---

