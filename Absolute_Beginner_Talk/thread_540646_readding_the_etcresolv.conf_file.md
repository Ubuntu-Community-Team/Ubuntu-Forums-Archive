---
title: "readding the /etc/resolv.conf file??"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by its_toby on 2007-09-01
Hey all,

I loaded the new 7.04 Kubuntu and when I openned the KPPP to add the ISP settings and error window can up and said that the /etc/resolv.conf file was missing.  Does anone have any Ideas as to how I can get that back??

thanks](*,)

---

### Post by southernman on 2007-09-01
<--- not a kde guy, but that's just weird regardless.

What happens if you do:

> sudo nano /etc/resolv.conf

in a terminal? Is the file empty?

---

### Post by taurus on 2007-09-01
Or maybe look to see if it is really there first.

```
ls -la /etc/resolv.conf
```

---

