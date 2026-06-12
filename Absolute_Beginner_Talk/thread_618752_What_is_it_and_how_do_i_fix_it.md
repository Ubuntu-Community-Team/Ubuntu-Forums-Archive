---
title: "What is it and how do i fix it????????"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by psb007 on 2007-11-20
I get this error when i do an update.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

What is it and how do i fix it? when i  'dpkg --configure -a' in terminal i get:

paul@ubuntu:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
paul@ubuntu:~$ 

hmmmmm is this a reinstall situation?

---

### Post by Paul820 on 2007-11-20
No, it's not a reinstall situation :lolflag: You just forgot the sudo at the beginning
> sudo dpkg --configure -a

---

### Post by cmnorton on 2007-11-20
> **psb007 said:**
> I get this error when i do an update.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

What is it and how do i fix it? when i  'dpkg --configure -a' in terminal i get:

paul@ubuntu:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
paul@ubuntu:~$ 

hmmmmm is this a reinstall situation?

Pretty sure you need a sudo in front of dkkg --configure -a.

---

### Post by psb007 on 2007-11-21
Thanks for the help

Man i feel dumb. Ha i need a vacation. :)

---

