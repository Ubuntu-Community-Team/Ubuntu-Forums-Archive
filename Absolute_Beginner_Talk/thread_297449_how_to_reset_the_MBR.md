---
title: "how to reset the MBR"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by ishkmi on 2006-11-11
Hi all,
i install the Ubuntu in my PC...which i already have windows XP
and i delete the Ubuntu partition  from the Windows XP but..now I cannot Load the Windows XP how can I edit the master boot record to load the Windows XP .... If someone can please help me..


thanks,
ishkmi

---

### Post by catlett on 2006-11-11
You need a Windows XP Installation cd. That cd has a recocery console on it. The recovery console has a command ```
FIXMBR
``` That will fix your windows mbr and allow you to boot to windows again. 
This shows the recovery console and the commands you can use to fix your mbr [http://www.geocities.com/kilian0072002/recconsole2.html](http://www.geocities.com/kilian0072002/recconsole2.html)
This is more detail onb how to get into the recovery console. [http://www.geocities.com/kilian0072002/recconsole1.html](http://www.geocities.com/kilian0072002/recconsole1.html)

---

### Post by MaceM on 2006-11-11
boot with your winXP install CD and load the "rescue console"
(you'll need your admin password)
then you can use
```

FIXMBR

```
and
```

FIXBOOT

```
to let it try and fix the mbr. it didn't always work for me though.

---

