---
title: "how do i change /dev/hda to /dev/dvd?"
date: 2006-06-18
forum: Absolute Beginner Talk
---

### Post by lime4x4 on 2006-06-18
For some reason ubuntu always list my dvd burners as /dev/hda and /devhdb
When trying to use apps like xdvdshrink it never runs cause it's always looking for /dev/dvd so what would be the best way of fixing this?

---

### Post by darkali on 2006-06-18
Just create a link to is by doing:

```
sudo ln -fs /dev/hda /dev/dvd
```

---

