---
title: "Ubuntu won't boot"
date: 2006-10-06
forum: Absolute Beginner Talk
---

### Post by ObeseOgre on 2006-10-06
When I boot ubuntu I get this message:

mount: Mounting/dev/hdd1 on /root failed:invalid arguement
...
/bin/sh: can't access tty; job control turned off

I searched the forums about a problem and I think its the same problem in this thread: [http://www.ubuntuforums.org/showthread.php?t=185396&page=2&highlight=Target+file+system+doesn%27t+have+%2Fsbin%2Finit](http://www.ubuntuforums.org/showthread.php?t=185396&page=2&highlight=Target+file+system+doesn%27t+have+%2Fsbin%2Finit)

Is there anyway I can boot through Live CD and fix it? 
(My primary master - DVD-RW / Secondary Slave - HDD with Ubuntu on it)

Thanks

---

### Post by ObeseOgre on 2006-10-06
I used the liveCD and did $sudo gparted
which showed me the harddrive ubuntu is installed on is in fact hdd1.  So now im confused as why it won't mount.

---

