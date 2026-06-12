---
title: "Change apache 2.0.55 root dir?"
date: 2006-10-06
forum: Absolute Beginner Talk
---

### Post by Ben Sprinkle on 2006-10-06
Anyone know how to change the root dir from /var/www?
I have tried:
```

apache -d newdir

```
Doesn't work.

---

### Post by Ben Sprinkle on 2006-10-06
Anyone?

---

### Post by az on 2006-10-06
Every site that is enabled is in your /etc/apache2/ configuration directory.  There are sites available and sites enabled.  Use the a2ensite to enable a new site.

If you just want to be simple, edit the default site config to point to a different root directory.

---

