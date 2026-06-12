---
title: "Network UPS Tools Packaging Problem"
date: 2009-09-17
forum: Apple Hardware Users
---

### Post by Caliph Alexander on 2009-09-17
I've got a Mac Mini G4/1.42gHz that I'm using as a small network server.  Mostly, it works flawlessly (kudos to those folks who still support PowerPC!), but one oddity is the NUT package.  I installed nut with apt-get, and configured it.  Then, I attempted to start it, and got nothing, at all.  Looking more deeply, I noticed that the NUT package is short a few important parts:

```
root@spud:~# dpkg-query --listfiles nut
/etc
/etc/nut
/etc/nut/nut.conf
/etc/nut/ups.conf.sample
/etc/nut/upsd.conf.sample
/etc/nut/upsd.users.sample
/etc/nut/upsmon.conf.sample
/etc/nut/upssched.conf.sample
/etc/init.d
/etc/init.d/nut
/etc/bash_completion.d
/etc/bash_completion.d/nut
```

Does anyone know what might have happened, here?

Thanks!

---

