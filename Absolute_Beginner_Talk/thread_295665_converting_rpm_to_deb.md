---
title: "converting rpm to deb"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by doh224 on 2006-11-08
hey.. how do I get the alien program, for converting rpm files to deb files?

---

### Post by qalimas on 2006-11-08
```
sudo aptitude update
sudo aptitude install alien
sudo alien file.rpm
```

---

### Post by steve.horsley on 2006-11-08
> sudo apt-get install alien
It's in the repositories. The chances are that whatever you are trying to install is in the repos too. What are you trying to install?

---

### Post by doh224 on 2006-11-08
arh nothing important. :) but thanks a lot you two ;)

---

