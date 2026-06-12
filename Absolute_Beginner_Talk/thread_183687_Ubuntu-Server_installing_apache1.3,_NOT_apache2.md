---
title: "Ubuntu-Server installing apache1.3, NOT apache2"
date: 2006-05-28
forum: Absolute Beginner Talk
---

### Post by Bultot on 2006-05-28
I'm not an experienced linuxuser. I just want to launch my ubuntu webserver with a neko virtual machine. ([http://www.nekovm.org)](http://www.nekovm.org)).

The problem is neko won't run on apache2.

With my current repositories I can only choose apache2 to install.
Which repository do I have to add for installing apache1.3 ?

Thanks

---

### Post by ifokkema on 2006-05-28
[QUOTE=Bultot]I'm not an experienced linuxuser. I just want to launch my ubuntu webserver with a neko virtual machine. ([http://www.nekovm.org)](http://www.nekovm.org)).

The problem is neko won't run on apache2.

With my current repositories I can only choose apache2 to install.
Which repository do I have to add for installing apache1.3 ?[/QUOTE]

Apache 1.3 is available from the universe repositories. If you want apache 1.3, and not apache2, run:
```
sudo apt-get remove apache2
sudo apt-get install apache
```
Hope this helps,

Ivo

---

### Post by Bultot on 2006-05-29
Thank you :)

---

