---
title: "tracker question"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by syalam on 2007-04-24
how can I get tracker to index everything from root and below? it is only indexing my home directory right now.

---

### Post by tom56 on 2007-04-24
I'm not sure that it can. Certainly it's not a good idea - indexing that much stuff would be a huge waste of resources. What are you looking for that isn't in /home? You can always try locate:

```
tom@scaleo-desktop:~$ locate xorg.conf
/etc/X11/xorg.conf~
/etc/X11/xorg.conf
/usr/share/ubuntu-docs/ubuntu/sample/xorg.conf_disablenvidialogo
/usr/share/ubuntu-docs/ubuntu/sample/xorg.conf_disablectrlaltbackspacegnome
/usr/share/man/man5/xorg.conf.5.gz
/var/lib/x11/xorg.conf.md5sum
/var/lib/x11/xorg.conf.roster
tom@scaleo-desktop:~$ 
```

---

### Post by jamiemcc on 2007-05-13
> **tom56 said:**
> I'm not sure that it can. Certainly it's not a good idea - indexing that much stuff would be a huge waste of resources. What are you looking for that isn't in /home? You can always try locate:

Its planned in tracker to offer systemwide searching of filenames by default so there will not be a need for locate.

The Home dir will of course still get the full indexing treatment including file contents whereas the system wide one by default will be limited to filename indexing only.

---

