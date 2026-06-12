---
title: "upper limit to a ext3 partition in Ubuntu?"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by Bob Walsh on 2006-07-10
Dispite help here I was unable to acces sda6, an 765 GB partition I'd set up on my new dell.

I'm reformatting it now via qtparted running from a Linux rescue disk, but I wondered, is that partition too big for Ubuntu to mount?

---

### Post by FredB on 2006-07-10
Theorically, ext3fs can manage up to 2 Tb (2 048 Gb).

[http://en.wikipedia.org/wiki/Ext3fs](http://en.wikipedia.org/wiki/Ext3fs)

Maybe a single partition of  765 Gb is too big ?

---

### Post by Bob Walsh on 2006-07-10
well, ext3 should be fine with that... I keep getting back a "only root can mount "...

---

### Post by MaximB on 2006-07-10
> **Bob Walsh said:**
> well, ext3 should be fine with that... I keep getting back a "only root can mount "...

so you already know what to do...log on as root or type sudo before the command and mount.

---

