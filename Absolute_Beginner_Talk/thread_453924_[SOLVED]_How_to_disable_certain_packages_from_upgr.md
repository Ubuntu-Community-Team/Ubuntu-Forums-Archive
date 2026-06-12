---
title: "[SOLVED] How to disable certain packages from upgrading with apt-get"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by be4truth on 2007-05-24
Hi Everybody,
how do I disable certain packages to be upgraded by apt-get. In YUM I know how to do but apt-get is new. Which config file is it?
Thx in advance
Juergen:KS

---

### Post by lazyart on 2007-05-24
echo "*packagename* hold" | sudo dpkg --set-selections

---

