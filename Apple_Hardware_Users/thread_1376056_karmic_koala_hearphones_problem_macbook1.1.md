---
title: "karmic koala hearphones problem macbook1.1"
date: 2010-01-08
forum: Apple Hardware Users
---

### Post by Fabioamd87 on 2010-01-08
Hi I've a problem with Karmic Koala and my macbook1.1
when i plugin hearphones I can't hear sound in it and in the speaker...

many thread suggest to use alsamixer but I've only this settings
[IMG]http://img694.imageshack.us/img694/5651/schermataa.png[/IMG]

I've NO alsa.conf setting in /etc/modprobe.d/

---

### Post by linuxopjemac on 2010-01-09
I can only advise you to install the alsa module backport:
```
aptitude install linux-backports-modules-alsa-karmic-generic
```

If that does not work, we will patch your alsa configuration file.

---

### Post by Fabioamd87 on 2010-01-09
Solved, maybe we should update the wiki?

---

### Post by linuxopjemac on 2010-01-10
That's not up to me. I am not part of the Ubuntu Mactel group. Maybe you can send it to one of those people.

---

