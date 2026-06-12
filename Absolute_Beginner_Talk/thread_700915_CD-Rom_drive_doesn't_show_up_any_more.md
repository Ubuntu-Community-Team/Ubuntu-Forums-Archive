---
title: "CD-Rom drive doesn't show up any more"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by Djalmahal on 2008-02-18
Hi,

i tried to make my ubuntu machine dual boot windows xp, it didn't work, but now the cd/dvd drive doesn't show up any more, meaning when i insert a cd/dvd it just doesn't react.

So, how do i solve it? If you need any command line output i'll be happy to send that.

Thanks
Andreas

---

### Post by spiderbatdad on 2008-02-18
is this an internal or external drive?
try running ```
sudo depmod -a
```

---

### Post by Djalmahal on 2008-02-18
If internal means built in, yes it is internal

What does your command do?

---

### Post by spiderbatdad on 2008-02-18
[http://linux.about.com/library/cmd/blcmdl8_depmod.htm](http://linux.about.com/library/cmd/blcmdl8_depmod.htm)

---

