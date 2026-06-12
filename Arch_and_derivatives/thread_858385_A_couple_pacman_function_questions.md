---
title: "A couple pacman function questions"
date: 2008-07-13
forum: Arch and derivatives
---

### Post by YodaMstr on 2008-07-13
I remember a thread on the official forums a while back that gave a command which listed the number of total installed packages and such as that.  I also remembered a command that listed true orphan packages which had not been explicitly installed.  Could someone point me in the right direction on these?  Also, is there a command to show the total size of all the packages installed so far?  Thanks.

---

### Post by Dr Small on 2008-07-13
I haven't searched, but this should do it.
For Total Packages:
```
pacman -Q | wc -l
```

For Orphans:
```
pacman -Qe | wc -l
```

---

### Post by kpkeerthi on 2008-07-14
To find the orphans, you should use
```
pacman -Qdt
```

---

