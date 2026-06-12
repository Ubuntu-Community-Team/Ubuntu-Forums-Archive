---
title: "Jaunty: adt746x module fails to load"
date: 2009-05-20
forum: Apple Hardware Users
---

### Post by moviemaniac on 2009-05-20
Hi guys,

another problem occured when I installed Jaunty on my brothers 12" PowerbookG4 (867MHz) today:

I wanted to load the adt746x to fix the problem of the machine getting really hot but the module won't load.

when I run "sudo modprobe therm-adt746x" I get the following error message:

```
FATAL: Error inserting therm_adt746x (/lib/modules/2.6.28-6-powerpc/kernel/drivers/macintosh/therm_adt746x.ko): No such device
```

any ideas? (and yes, the kernel-module is there where it should be...)

thanks in advance,
Klaus

//edit: nevermind, it's one of those danged Nvidia-Powerbooks and the module only works for the ATI-ones :(

---

