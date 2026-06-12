---
title: "Sudo is away!"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by hz1840821 on 2006-11-05
I got a big trouble with my ubuntu. All user lost root privileges and therefore cannot run sudo. As result my linux refuse all string preceeded by sudo. If I type for example in the terminal
$ sudo synaptic
the line is ignored, nothing happens. This is very bad, it seems a problem with no solution.

Can anybody help me?

Franco

---

### Post by taurus on 2006-11-05
Boot into recovery mode from GRUB and edit /etc/group and put your login name in both adm & admin.

```
nano -Bw /etc/group
```
Reboot and you are back to sudo away...

---

