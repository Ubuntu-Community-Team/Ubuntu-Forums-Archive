---
title: "x window fails, goes to unix"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by murpc004 on 2006-11-22
Hi
My ubuntu has been working fine up til now, but my gui for some strange reason does not come up, it goes to unix login :-k, and while that is better then nothing, i'd prefer gui!

What's wrong????? ](*,) 
murpc004

---

### Post by IYY on 2006-11-22
Do you get some sort of error, or does it just not show up? Try running the program

```
gdm
```

or


```
startx
```

(after logging in)

---

### Post by taurus on 2006-11-22
Log in with your username and password and try to run

```
sudo /etc/init.d/gdm start
```

---

