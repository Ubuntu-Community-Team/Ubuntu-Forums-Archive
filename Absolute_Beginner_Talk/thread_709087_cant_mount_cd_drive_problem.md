---
title: "cant mount cd drive problem"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by bigfoot1979 on 2008-02-27
hi. having a problem mounting my cdrom drive. xubuntu alternate iso install of gutsy gibbon. 
it gives me the option to manually choose a module for accessing the cdrom but i dont know what to choose.... none, cdrom,gscd etc. my dvd rom hardware is a hitachi gd s250.

many thanks for any help. detirmined to get this working.

h

---

### Post by jan quark on 2008-02-27
can you please post your fstab file

```
cat /etc/fstab
```

---

### Post by bigfoot1979 on 2008-02-27
hope i have done this right...l

it says 

none   /dev   devfs  defaults 0 0
none /dev/pts   devpts   defaults  0  0
none   /proc   proc defaults  0 0
none  /sys   sysfs  noauto 0 0

i got this info from typing your code into the busybox shell during the install.

hope its ok.

thanks

---

