---
title: "changing read-only"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by Nessa on 2007-07-13
My 60gb partition in ext3 format is read-only. How can I change that?

---

### Post by felicity on 2007-07-13
I use: 

```

sudo chmod -R a+rwx /media/storage

```

but change /media/storage to wherever your drive is mounted.

---

### Post by Nessa on 2007-07-13
sudo: timestamp too far in the future: Jul 13 22:42:48 2007

Didn't work. :(

---

