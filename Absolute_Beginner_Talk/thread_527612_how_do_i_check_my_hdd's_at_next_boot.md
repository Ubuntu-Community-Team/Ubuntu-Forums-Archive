---
title: "how do i check my hdd's at next boot?"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by jmate24 on 2007-08-16
how do i check my hdd's at next boot? they have a few errors on them; mostly with photos.

and can anyone help me download and setup Firestarter and ClamAV. Through Synaptic.

thanks for your time:)

jmate24

---

### Post by overdrank on 2007-08-16
> **jmate24 said:**
> how do i check my hdd's at next boot? they have a few errors on them; mostly with photos.

and can anyone help me download and setup Firestarter and ClamAV. Through Synaptic.

thanks for your time:)

jmate24

HI I can help with firestarter
```
sudo apt-get install firestarter
``` 
In the terminal
You can also run fsck from the live cd.

---

### Post by yabbadabbadont on 2007-08-16
To force a filesystem to be checked on next boot, you just need to create a file called "forcefsck" in the root directory of that filesystem's mount point.  Example:  I have /, /boot, and /home as three separate partitions.  To force /home to be checked on next boot, I would run (in a terminal window) "sudo touch /home/forcefsck".  For root, "sudo touch /forcefsck".  And so on.

---

