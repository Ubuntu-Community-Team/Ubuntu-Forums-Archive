---
title: "[SOLVED] folder permissions var/www"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by DaveyG on 2007-03-11
im trying to delete the files from var/www but it says i dont have permission, is there any way i can change the permissions so that i can add and delete files from there?

Davey

---

### Post by taurus on 2007-03-11
Applications -> Accessories -> Terminal
```
sudo rm **filename**
```

---

### Post by soul814 on 2007-03-11
ALT + F2, type gksudo nautilus

then you can browse there and delete, what i did instead was

1) ALT + F2, type gksudo nautilus
2) Browse to /var/www
3) Right click Properties
4) Group Access >> Set to your User, set Read and Write Access

---

### Post by DaveyG on 2007-03-11
Thank you, but is there a sudo command to remove folders. or one to add files to var/www?..

Many thanks

---

