---
title: "[SOLVED] how do i create a symolic link to run at startup?"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by e1ektrob0y on 2008-01-18
I have to run ```
ln -s /dev/cdrom1 /dev/dvd
``` to make my dvd drive work with gxine. how do i run this command at startup?

---

### Post by jordanmthomas on 2008-01-18
put it in /etc/rc.local
and it'll be run at boot by root.

edit
At least that works in Arch.  Ubuntu seems to have more and more weird things about it the more I learn.
If not, there's other ways too.

---

### Post by dcstar on 2008-01-18
> **e1ektrob0y said:**
> I have to run ```
ln -s /dev/cdrom1 /dev/dvd
``` to make my dvd drive work with gxine. how do i run this command at startup?
```

gksudo gedit /etc/rc.local
```

---

### Post by PinkFloyd102489 on 2008-01-18
I was going to suggeset a separate script to be run with the gnome session manager, but rc.local works much better :-P

---

