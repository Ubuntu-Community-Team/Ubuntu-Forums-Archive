---
title: "Mounting /dev/shm, ppl said tmpfs on... but mine is devshm on... ????"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by kurniawands on 2006-07-26
any idea why ?

i did...

**:~$ sudo gedit /etc/fstab**  *and add...*

**tmpfs /dev/shm tmpfs defaults 0 0**

after save...

**:~$ mount /dev/shm**  *and get this...*
[B]mount: according to mtab, devshm is already mounted on /dev/shm
mount failed[/B]

then when i...
**:~$ mount | grep "shm"**  *and get this...*
**devshm on /dev/shm type tmpfs (rw)**

mean POSIX not suported or handled different way or what ???:-k

---

