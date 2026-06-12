---
title: "/dev/sda1 has been mounted 26 times without being checked..."
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by Eriks_Knor on 2007-11-26
...check forced.

Can somebody tell me what that means. I've gotten this at boot up, it runs, then my laptop boots up. Is there some kind of maintenance I need to do?

---

### Post by jken146 on 2007-11-26
The file system checking utility fsck runs automatically every 30 boots, to check the integrity of your ext3 file systems.  You can disable this if you wish or set the interval to another number than 30.  See here: [http://ubuntuforums.org/showthread.php?t=590123&highlight=disable+fsck](http://ubuntuforums.org/showthread.php?t=590123&highlight=disable+fsck)

---

### Post by Eriks_Knor on 2007-11-26
Thanks very much! That explains a lot.

---

