---
title: "mount cdrom, bind in fstab"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by cnschulz on 2007-06-25
Hi (again) ;-)

I am wondering how/if I can mount a cd iso using fstab. I know how to use the mount command to do this but i am unsure of the format used to achieve this in fstab.

Id just like to have the cd iso mounted at boot time

Similarly, id like to do a --bind in fstab as well... is that possible?

cheers

c.

---

### Post by Sokraates on 2007-06-26
According to the Linuxquestions.org-Wiki the command is
```
/image.iso /target/folder iso9660 ro,loop,auto 0 0
```

---

### Post by alienexplorers on 2007-06-26
You could also try:

> /dev/hdc        /target/folder   udf,iso9660 user,noauto     0       0

---

### Post by Sokraates on 2007-06-27
@ alienexplorers: He is talking about a cdrom-iso, not a cdrom-drive. Or am I missing something?

@cnschulz: Oooops, forgot about your second question. This should to the trick:
```
/old/folder  /new/folder  none  bind 0 0 
```

---

### Post by cnschulz on 2007-06-27
thank you all.

works fine!

c.

---

