---
title: "Installation path change, possible?"
date: 2005-07-06
forum: Absolute Beginner Talk
---

### Post by ozzie123 on 2005-07-06
Hello, I have just realized, after some updates, the current drive of my linux installation is no longer sufficient. So I'm installing a new harddrive to coupe with the storage problems.

The problem is, each time I tried to install a linux application or update, it always install on the old drive. Is it possible to move the installation path from my old drive to my new drive (changing /usr/bin probably?)

Thanks

---

### Post by bunced on 2005-07-07
I can't see a way of doing it without reinstalling. Drives are definined in /etc/fstab and if you change that, you will have to move the contents over too.

---

