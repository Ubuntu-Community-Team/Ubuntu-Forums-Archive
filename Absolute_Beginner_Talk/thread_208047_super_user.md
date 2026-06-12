---
title: "super user"
date: 2006-07-02
forum: Absolute Beginner Talk
---

### Post by ckonrad on 2006-07-02
how do you get into superuser when in a terminal i am used to just doing su and then typing in my password in other forms of linux but when i do that in ubuntu it denies me?

---

### Post by aysiu on 2006-07-02
If you get tired of typing the word *sudo* for several commands in a row, just type ```
sudo -s
``` and you'll have a root terminal instead.

---

### Post by ckonrad on 2006-07-02
ok thanks that worked, i thought all linux' were the same when it came to commands.


[QUOTE=aysiu]If you get tired of typing the word *sudo* for several commands in a row, just type ```
sudo -s
``` and you'll have a root terminal instead.[/QUOTE]

---

### Post by joshrobinson on 2006-07-02
[QUOTE=ckonrad]how do you get into superuser when in a terminal i am used to just doing su and then typing in my password in other forms of linux but when i do that in ubuntu it denies me?[/QUOTE]

i know aysiu will bust my balls on this one.. but if you really are prone to using su

```
sudo passwd
```
set the password you want to use when you type su

and then use su as u normally would

---

