---
title: "Uninstall Lilo"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by cancaseiro on 2007-07-19
Does anyone know good method to uninstall Lilo with the help of live Linux cd? I tried:

```
/mnt/sbin/lilo -u
```

but it said

```
root@ubuntu:/mnt# /mnt/sbin/lilo -u
/mnt/sbin/lilo.real: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /mnt/sbin/lilo.real)
```

mnt is there because that's where I mounted my Linux partition. I also tried to install this GLIBC_2.4 but it failed and didn't install. So I would appreciate  it much if someone can help me here. [-o<

---

### Post by FleetAdmiral74 on 2007-07-19
This thread, [http://www.linuxquestions.org/questions/showthread.php?t=120655](http://www.linuxquestions.org/questions/showthread.php?t=120655), seems to say if you just install grub it will overwrite the mbr, so you should be good to go.

---

### Post by cancaseiro on 2007-07-20
> **FleetAdmiral74 said:**
> This thread, [http://www.linuxquestions.org/questions/showthread.php?t=120655](http://www.linuxquestions.org/questions/showthread.php?t=120655), seems to say if you just install grub it will overwrite the mbr, so you should be good to go.

Yes, I did that and now the system works. Only downside is that first boot device is Mac OS X but no problem, I can live with that. Thanx! :)

---

