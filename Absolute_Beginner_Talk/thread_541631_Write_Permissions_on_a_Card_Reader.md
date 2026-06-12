---
title: "Write Permissions on a Card Reader"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by Blue_T0oth on 2007-09-03
been looking this problem up a while now, every1 seems to recomend formatting ur card, though i'm not sure how to do that... and on my phone theres no options of what to format to just formats for a fat16, i'm using a lexar 2.0 multicard reader and it works fine... just cant play with ne of the data on the card other than coping.... ne suggestions??

---

### Post by pizzutz on 2007-09-03
Check to see if it is either mounted read only 

sudo mount

if not, check the permissions to see if it is mounted with write permissions for underpriveleged users

ls -la /media

---

### Post by Yizi on 2007-09-03
> **pizzutz said:**
> Check to see if it is either mounted read only 

sudo mount

if not, check the permissions to see if it is mounted with write permissions for underpriveleged users

ls -la /media

I check mine and its:

```
dr-xr-xr-x  1 root root 143360 2007-09-01 18:10 80 GB

```

How can i change the permission?

---

