---
title: "modules"
date: 2005-11-25
forum: Absolute Beginner Talk
---

### Post by soonindallas on 2005-11-25
during the boot process I see "initialising modules failed"

what log or file can I inspect to find out about modules that may or may not have loaded or been initialised at boot time ?

---

### Post by soonindallas on 2005-11-28
bump

---

### Post by Brunellus on 2005-11-28
logs are in /var/log

to list the modules loaded on your system, use

```
$lsmod
```

since there are usally loads of 'em, I usually pipe it to less:

```
$ lsmod | less
```

---

### Post by az on 2005-11-28
[QUOTE=soonindallas]during the boot process I see "initialising modules failed"

what log or file can I inspect to find out about modules that may or may not have loaded or been initialised at boot time ?[/QUOTE]


use the log tool to look at /var/log/messages.  You will be able to see the point at which it boots, and just go forward from there.

---

