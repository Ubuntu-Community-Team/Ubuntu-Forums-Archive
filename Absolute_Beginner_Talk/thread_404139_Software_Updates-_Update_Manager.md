---
title: "Software Updates- Update Manager"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by Kevin Funnell on 2007-04-08
I receive the following Pop-Up when using Update Manager
/home/kevin/respository.jpg
the text within the box is:

[COLOR="Red"]http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz: Sub-process gzip returned an error code (1)
[/COLOR]

Is this a problem and how can I rectify it so tha all updates work correctly.

Thanks in Advance,

Old Kevin

---

### Post by eentonig on 2007-04-08
A link to a local picture won't be usefull for anyone except you.

---

### Post by OffHand on 2007-04-08
Try

```
sudo apt-get install -f
```

---

