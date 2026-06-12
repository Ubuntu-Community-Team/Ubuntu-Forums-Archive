---
title: "[SOLVED] Unable to mount DVD"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by intense.ego on 2007-10-27
My friend burned a dvd with some files on it and gave it to me. When i put it in my dvd drive, ubuntu tells me:

Invalid mount option when attempting to mount the volume 'UDF Volume'.

what is wrong and how do i fix the problem? is it something to do with my dvd drive?

---

### Post by Malta paul on 2007-10-27
Hi, I would first try another DVD in your computer, that way you will know if your DVD drive is OK.
Also I would ask your friend to try the disk he gave you in his computer and see if it works.
Good luck:wink:

---

### Post by intense.ego on 2007-10-28
I discovered the problem was that it was a newer type of live filesystem (UDF) that is not compatible with ubuntu.

---

### Post by juliwoodbcn on 2008-05-21
apt-get install udftools

---

