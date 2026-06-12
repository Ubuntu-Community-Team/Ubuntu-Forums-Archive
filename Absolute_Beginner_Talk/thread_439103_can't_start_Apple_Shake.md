---
title: "can't start Apple Shake"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by degro on 2007-05-10
hello people. i got a really big problem.

i downloaded Apple Shake trial from the Apple website and it's .dmg. Is that an OS X extension? 

Anyway, i got another version from a friend of mine, 4.00.607 and it won't start.

i found out that its dependencies are CSH and TCSH (i really don't know what those are) and that it starts like going to the BIN folder and typing CSH SHAKE. i did it and... :
```
root@glue:/home/shake-v4.00.0607/bin# csh shake
/home/shake-v4.00.0607/bin/shkx.exe: Permission denied.
```

could somebody please help me? i really want to try it out, as i heard it is the best compositing software for linux... and i really am into ubuntu now.

---

### Post by taurus on 2007-05-10
Maybe you need to set it to executable permission first before you can run it!

```
chmod 755 shake
```

---

