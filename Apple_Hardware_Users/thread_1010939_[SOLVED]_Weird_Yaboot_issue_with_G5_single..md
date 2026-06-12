---
title: "[SOLVED] Weird Yaboot issue with G5 single."
date: 2008-12-14
forum: Apple Hardware Users
---

### Post by casbahdk on 2008-12-14
I have been experiencing some issues with OS X Leopard and had to reinstall 10.5.5 and then use Time Machine to get the rest of my system back on track. Since I did this, Yaboot doesn't show at boot time anymore. The weird thing is that if I hold down the option (alt) key until I get a graphic screen showing the boot partitions that I have, I can choose the Linux icon and then Yaboot kicks in. I can choose which boot partition to choose from, this time from Yaboot. My Ubuntu 8.04 system boots just fine after that.what do I have to do to sort out Yaboot?

Cheers

---

### Post by tiresia on 2008-12-14
Boot Linux holding down the opt - key.
Open a terminal and run```
ybin -v
```
Restart to check that yaboot works again

For more info
[http://ubuntuforums.org/showthread.php?t=994882](http://ubuntuforums.org/showthread.php?t=994882)

---

### Post by casbahdk on 2008-12-14
[QUOTE=tiresia;6367506]Boot Linux holding down the opt - key.
Open a terminal and run```
ybin -v
```
Restart to check that yaboot works again

Yes! That seems to have done it. Thanks.:D

---

### Post by tiresia on 2008-12-14
ok, please, mark this thread as solved

---

